#### 条款13：以对象管理资源



##### RAII 资源获取即初始化（Resource Acquisition Is Initialization）

```c++
思想有两点：
    1.使用对象管理资源，获取资源后立即放进对象内进行管理。
    2.对象的析构函数确保资源的释放：利用对象离开作用域后调用析构的原理
    
典型的例子：智能指针
    智能指针的缺点：对于数组类型，不会调用delete[].所以需要手工添加deleter
    如： std::shared_ptr<std::string> ptr(new std::string[10],[](std::string* p){delete[] p; });
```



#### 条款14：在资源管理类中小心coping行为

```
在设计RAII类的时候，要小心处理拷贝动作（拷贝构造，拷贝赋值）
因为RAII是对资源的包装，负责对资源的操作和销毁，当RAII对象产生copy动作后，必然影响到资源的管理
所以，不要使用编译器生成默认版本的拷贝动作函数，一定要重写。

根据实际情况可选用以下策略：
1.禁止复制操作：
	如设置为=delete
2.使用引用计数：
	如果允许资源共享，设置引用计数，最后一个持有该资源的RAII对象负责销毁或者处理资源
	如RAII包装锁，当获取到锁后，RAII对象进行lock(),RAII对象使用引用计数管理，当最后一个RAII对象销毁时，负责对锁的unlock()操作。(可以使用智能指针包装锁，并传入deleter，负责unlock并delete)
3.复制底部资源：
	如果资源允许被复制多份，可以深拷贝创建出新的资源副本。
4.转移管理权:
	如unique_ptr
```



#### 条款15：在资源管理类中提供对原始资源的访问

即RAII类，应该实现一个返回原始资源的渠道。如智能指针的get() -> *操作符重载

```
总结：
1.对于指针类型，重载指针特有的操作符，如-> * &等
2.开放一个接口，如get()，但是有资源暴露的隐患，破坏了封装
3.转换函数 operator type()
https://blog.csdn.net/lihao21/article/details/54098169

选取以上哪个方法，没有定法。一般get方法的方式比较流行。虽然说会破坏封装，但是RAII的本意是为了确保资源的释放。唯一可以遵循的原则是，让接口更容易使用，不易被误用。
```



#### 条款16：成对使用new和delete时要采取相同形式

```
对于new操作：
1.如果new的目标是对象，首先operator new分配对象的heap空间，调用对象的默认构造器
2.如果new的目标是数组，数组长度为n，首先operator new分配n个对象的heap空间，调用n次对象的默认构造器。（编译器会在第一个对象之前位置，开辟一个空间记录数组个数n）

对于delete操作
1.delete 调用对象析构，回收内存空间
2.delete[] 调用n个对象析构，回收内存空间。

```



#### 条款17：以独立语句将newed对象置入智能指针

```
processWidget(shared_prt<Widget>(new Widget), priority()); 
这种操作有危险，因为在调用processWidget()之前，必然完成：1.new Widget 2.shared_prt<Widget>() 3.priority()的调用。
虽然编译器的实现不同，三者的顺序没有绝对的顺序，但是1.new Widget必然先于 2.shared_prt<Widget>() 完成。

假如顺序是：
1.new Widget 
2.priority()的调用
3.shared_prt<Widget>()

如果在2处出现了抛出异常栈展开，刚new出来的对象，尚未被智能指针管理，此时造成内存泄漏

所以，对于new的操作，以独立语句完成
shared_prt<Widget> pw(new Widget);
processWidget(pw,priority());

```

