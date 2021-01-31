### Effective C++ 笔记

##### 目录

[条款1：视C++为一个语言联邦](https://blog.csdn.net/kangroger/article/details/41870771#t0)

[条款2：尽量以const、enum、inline替换#define](https://blog.csdn.net/kangroger/article/details/41870771#t0)

[条款3：尽可能使用const](https://blog.csdn.net/kangroger/article/details/41870771#t0)

✔[条款4：确定对象使用前已先被初始化](https://blog.csdn.net/kangroger/article/details/41870771#t0)

✔[条款5：了解C++默认编写并调用哪些函数](https://blog.csdn.net/kangroger/article/details/41986049#t0)

[条款6：若不想使用编译器自动生成的函数，就该明确拒绝](https://blog.csdn.net/kangroger/article/details/41986049#t0)

[条款7：为多态基类声明virtual析构函数](https://blog.csdn.net/kangroger/article/details/41986049#t0)

[条款8：别让异常逃离析构函数](https://blog.csdn.net/kangroger/article/details/41986049#t0)

[条款9：绝不在构造和析构过程中调用virtual函数](https://blog.csdn.net/kangroger/article/details/41986049#t0)

[条款10：令operator=返回一个reference to *this](https://blog.csdn.net/kangroger/article/details/42433437#t0)

[条款11：在operator=中实现“自我赋值”](https://blog.csdn.net/kangroger/article/details/42433437#t0)

[条款12：复制对象时勿忘其每一部分](https://blog.csdn.net/kangroger/article/details/42433437#t0)

[条款13：以对象管理资源](https://blog.csdn.net/kangroger/article/details/42526187#t0)

[条款14：在资源管理类中小心coping行为](https://blog.csdn.net/kangroger/article/details/42526187#t0)

[条款15：在资源管理类中提供对原始资源的访问](https://blog.csdn.net/kangroger/article/details/42526187#t0)

[条款16：成对使用new和delete时要采取相同形式](https://blog.csdn.net/kangroger/article/details/42717889#t0)

[条款17：以独立语句将newed对象置入智能指针](https://blog.csdn.net/kangroger/article/details/42717889#t0)

[条款18：让接口容易被正确使用，不容易被误用](https://blog.csdn.net/kangroger/article/details/42777713#t0)

[条款19：设计class犹如设计type](https://blog.csdn.net/kangroger/article/details/42777713#t0)

[条款20：宁以pass-by-reference-to-const替换pass-by-value](https://blog.csdn.net/kangroger/article/details/42965331#t0)

[条款21：必须返回对象时，别妄想返回其reference](https://blog.csdn.net/kangroger/article/details/42965331#t0)

[条款22：将成员变量声明为private](https://blog.csdn.net/kangroger/article/details/43501669#t0)

[条款23：宁以non-member、non-friend替换member函数](https://blog.csdn.net/kangroger/article/details/43501669#t0)

[条款24：若所有参数皆需要类型转换，请为此采用non-member函数](https://blog.csdn.net/kangroger/article/details/43501669#t0)

[条款25：考虑写出一个不抛出异常的swap函数](https://blog.csdn.net/kangroger/article/details/43677283)

[条款26：尽可能延后变量定义式的出现时间](https://blog.csdn.net/kangroger/article/details/43743531#t0)

[条款27：尽量少做转型动作](https://blog.csdn.net/kangroger/article/details/43743531#t0)

[条款28：避免返回handles指向对象内部成分](https://blog.csdn.net/kangroger/article/details/43883305#t0)

[条款29：为“异常安全”而努力是值得的](https://blog.csdn.net/kangroger/article/details/43883305#t0)

[条款30：透彻了解inlining的里里外外](https://blog.csdn.net/kangroger/article/details/43909975)

[条款31：将文件间的编译依存关系降至最低](https://blog.csdn.net/kangroger/article/details/43919645)

[条款32：确定你的public继承塑模出is-a关系](https://blog.csdn.net/kangroger/article/details/43941673#t0)

[条款33：避免遮掩继承而来的名称](https://blog.csdn.net/kangroger/article/details/43941673#t0)

[条款34：区分接口继承和实现继承](https://blog.csdn.net/kangroger/article/details/43958247)

[条款35：考虑virtual函数以外的其他选择](https://blog.csdn.net/kangroger/article/details/44024109#t0)

[条款36：绝不重新定义继承而来的non-virtual函数](https://blog.csdn.net/kangroger/article/details/44087967#t0)

[条款37：绝不要重新定义继承而来的缺省参数值](https://blog.csdn.net/kangroger/article/details/44087967#t0)

[条款38：通过复合塑模树has-a 或“根据某物实现出”](https://blog.csdn.net/kangroger/article/details/44137943#t0)

[条款39：明智而审慎的使用private继承](https://blog.csdn.net/kangroger/article/details/44137943#t0)

[条款40：明智而审慎的使用多重继承](https://blog.csdn.net/kangroger/article/details/44161773)

[条款41：了解隐式接口和编译期多态](https://blog.csdn.net/kangroger/article/details/44182087#t0)

[条款42：了解typename的双重意义](https://blog.csdn.net/kangroger/article/details/44182087#t0)

[条款43：学习处理模板化基类内的名称](https://blog.csdn.net/kangroger/article/details/44205331)

[条款44：将与参数无关的代码抽离templates](https://blog.csdn.net/kangroger/article/details/44228405#t0)

[条款45：运用成员函数模板接受所有兼容类型](https://blog.csdn.net/kangroger/article/details/44228405#t0)

[条款46：需要类型转换时请为模板定义非成员函数](https://blog.csdn.net/kangroger/article/details/44246535#t0)

[条款47：请使用traits class表现类型信息](https://blog.csdn.net/kangroger/article/details/44246535#t0)

[条款48：认识template元编程](https://blog.csdn.net/kangroger/article/details/44264053)

[条款49：了解new-handler的行为](https://blog.csdn.net/kangroger/article/details/44280793)

[条款50：了解new和delete的合理替换时机](https://blog.csdn.net/kangroger/article/details/44346281)

[条款51：编写new和delete时需固守常规](https://blog.csdn.net/kangroger/article/details/44497247)

[条款52：写了placement new也要写placement delete](https://blog.csdn.net/kangroger/article/details/44648189)

[条款53：不要轻忽编译器的警告](https://blog.csdn.net/KangRoger/article/details/44684435#t0)

[条款54：让自己熟悉包括TR1在内的标准程序库](https://blog.csdn.net/KangRoger/article/details/44684435#t1)

[条款55：让自己熟悉Boost