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
    Update(非左手表达式)
        a++
        a--
        --a
        ++a
    Unary(单目运算)
        delete reference
        void 
        typeof
        +a
        -a
        ～a
        !a
        await a
    Exponental(右结合)
        **
    Multiplicative
        * / %
    Additive
        + -
    Shift
        << >> >>>
    Relationship
        < > <= >= instanceof in
    Equality
        == != === !==
    Bitwise
        & ^ |
    Logical
        && ||
    Conditional
        ? :
    
JS运行时的设施 - reference

    存在于运行时中的js类型(标准中的类型,非语言中的类型)
    一个reference分为两个部分,object和key,记录了member运算的前半部分和后半部分
    delete, assign运算会用到reference类型


JS表达式的类型转换

    a + b
    "false" == flase
    a[o] = 1
    
             Number String Boolean Undefined Null Object Symbol
    Number                  0 false               boxing
    String                 "" false               boxing
    Boolean  flase 0 'true'                       boxing
             true 1  'false'  
    Undefined NaN   'Undefined' false
    Null       0      'null'    false
    Object   VauleOf  vauleOf
                      toString
    Symbol                                        boxing

    拆箱操作 - Unboxing
        ToPremitive
            toString
            vauleOf
            Symbol.toPremitive

    
    
