学习笔记

JS语法树与运算符的优先级关系
    Member
        a.b
        a[b]
        foo`string`
        super.b
        super['b']
        new.target
        new Foo()
    New
        new foo
    Call
        foo()
        super()
        foo()['b']
        foo().b
        foo()`abc`
    

JS运行时的设施 - reference
    存在于运行时中的js类型(标准中的类型,非语言中的类型)
    一个reference分为两个部分,object和key,记录了member运算的前半部分和后半部分
    delete, assign运算会用到reference类型





