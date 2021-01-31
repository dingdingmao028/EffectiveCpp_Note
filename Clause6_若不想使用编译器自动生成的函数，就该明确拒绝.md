#### 若不想使用编译器自动生成的函数，就该明确拒绝



##### 1.如果我们的类是独一无二的，比如unique_ptr一样，就不允许存在operator=() 所以解决办法：

```c++
1. 最方便的方法，c11的delete
class example{
public:
	void operator=(const example& inst)=delete;
}

2.定义为私有，并且不声明
class example{
private:
	void operator=(const example& inst);	
}
//1.编译器不会默认生成 2.设为私有无法被类外调用 3.不声明即不实现

3.设置一个父类，父类的相应的函数设置为私有
class uncopyable(){
    private:
	void operator=(const example& inst){//....}	
}
class example:public uncopyable {
	//编译器若想为example生成默认的拷贝赋值，首先要调用父类的拷贝赋值，由于是私有的，获取不到，从而无法生成生成默认的拷贝赋值
}
```

