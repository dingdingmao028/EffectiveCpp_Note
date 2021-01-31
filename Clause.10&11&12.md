#### Clause10 令operator=返回一个reference to *this

```c++
即链式操作，如std::string s1; s1.append("1").append("2");
实现以上功能，在operator xxx()操作符重载，返回当前对象的引用。
    如： class examlpe{
        public:
        examlpe& operator=(const example& inst){
             //...
            return this;
         	}              
    	}


```



#### Clause11 在operator=中实现“自我赋值”

```c++
class example{
public:
	example& operator=(const example& inst){
        //...
        return this;
    }

}
如果
example s1;
s1=s1; //自己赋值给自己，结果会怎样？

很多情况下，我们无法避免对象赋值给自己。
如：一个子类对象的指针，分别sub& s1=new sub; base* ptr=&s1; 其实s1和ptr1是同一个对象，如果ptr1=&s1 即自我赋值
    
这种自我赋值会出现危险：
class example{
public:
    example():s(new std::string("111"));
	example& operator=(const example& inst){
        delete this.s;					//因为inst.s 和this.s是同一个对象
        this.s=new std::string(inst.s); //inst.s被删除了，此时再读取，就会段错误
        return *this;
    }
    std::string* s;
}


改进方法：即判断是否是同一对象
    example& operator=(const example& inst){
        if(this==&inst) return this;	//判断
        delete this.s;					
        this.s=new std::string(inst.s);
        return *this;
    }

改进引申：上面的改进有个问题，如果new的动作失败抛出异常，this.s仍然是个空指针。
    改进：
    example& operator=(const example& inst){
        if(this==&inst) return this;
    	std::string* temp=this.s	//暂存当前的指针		
        this.s=new std::string(inst.s); //new出新的对象
    	delete temp ;	//如果new失败了，抛出异常栈展开，不会运行到此处 this.s仍然存在。 如果new成功了，再删除暂存指针
        return *this;
    }
    
    
    
```

### todo: copy and swap没看





#### Clause12 复制对象时勿忘其每一部分

##### 在拷贝构造和拷贝赋值函数中，我们需要：

1.确保每一个成员变量不可遗漏的复制

2.正确处理指针和引用类型，避免浅拷贝，造成两个对象共享同一个资源

3.处理拷贝过程中出现的问题，如对象复制给自己，new出现异常等

4.待总结...

```c++
问题1：
当我们重载并且完善了拷贝构造和拷贝赋值函数，当类中新添加了成员变量，勿忘更新这两个函数，确保对象中的成员变量完整无缺的复制

问题2：
如果子类继承了父类，子类的对象自然继承了父类的对象中的变量。勿忘在这两个函数调用父类的拷贝构造或者拷贝赋值

class base{
public:
 //...各种函数
};

class sub: base{
public:

    sub(sub& ele): base(ele){	//子拷贝构造必须调用父类的拷贝构造，将传进来的ele中的父类部分一并拷贝。如若不然，子类拷贝构造将调用父类的默认构造初始化变量
		//...
    }
    
    void operator=(sub& ele) {
        //...
        base::operator=(ele);	//子类的拷贝赋值函数必须调用父类的拷贝赋值函数，否则仅仅更新了子类的成员，父类对象中的成员仍就是之前的内容。
        //...
    };
};
```

