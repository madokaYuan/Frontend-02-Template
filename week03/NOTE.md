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

    装箱转换 - Boxing
        Number  new Number(1) 1
        String new String('a') a
        Boolean new Boolean(true) true
        Symbol new Object(Symbol('a')) Symbol('a')

JS的语句(完成控制流程,确定执行顺序)

    语句
        简单语句 - 不会再容纳其他语句的语句(有副作用)

            ExpressionStatement
            EmptyStatement
            DebuggerStatement
            ThrowStatement

            ContinueStatement
                [[type]]: break continue
                [[vaule]]: -
                [[target]]: label

            BreakStatement
                [[type]]: break continue
                [[vaule]]: -
                [[target]]: label

            ReturnStatement

        组合语句(有结构关系)

            BlockStatement 
                {
                    ...
                }
                [[type]] : normal
                [[vaule]] : --
                [[target]] : --

            IfStatement

            SwitchStatement
                [[type]]: break continue
                [[vaule]]: -
                [[target]]: label

            IterationStatement 
                [[type]]: break continue
                [[vaule]]: -
                [[target]]: label
                    while
                    do while
                    for ;;
                    for in
                    for of
                    for await(of)

            WithStatement

            LabelledStatement - for laballed break or continue
                [[type]]: break continue
                [[vaule]]: -
                [[target]]: label

            TryStatement - try catch finally
                [[type]]: return
                [[value]]: -
                [[target]] : label

        声明

            FunctionDeclaration
                function
                function * : genertator
                async function
                async function * : async genertator

            GeneratorDeclaration

            AsyncFunctionDeclaration

            VariableDeclaration
                声明 + 实际计算

            ClassDeclaration - 声明之前使用会报错
                class

            LexicalDeclaration - 声明之前使用会报错
                const
                let

    运行时

        语句执行结果记录 - 是否返回?返回值?
            每一个语句由JS引擎执行之后产生Completion Record
            [[type]]:normal,break,continue,return,throw
            [[vaule]]:基本类型
            [[target]]:label

        作用域相关

    预处理

        预处理是指在一段代码执行之前 JS引起会对代码本身做一次预先处理
        所有的声明,例如var,const,let都会进行预处理,把声明的变量变为一个局部变量,
        const,let在后方声明会抛错,可以被try catch处理

    作用域(非运行时)

        作用域链来自es3,早期的js设计中的var,function作用范围是所在的整个函数体
        const,let的作用域在所在的block {}

    宏任务与微任务(执行的粒度在运行时的表示)

        宏任务
        微任务(promise)
        函数调用(execution context)
        语句/声明(completion record)
        表达式(reference)
        直接量/变量/this

    


    
    
    
