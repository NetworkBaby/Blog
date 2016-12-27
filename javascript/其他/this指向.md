# this指向

### 全局this

相当于window

    console.log(window == this)
    //true
    
### 函数this

函数里面的this一般指全局this

    var a = "a";
    
    function change(){
        this.a = "b";
    }
    
    console.log(a); //a
    change();
    console.log(a); //b
    
如果使用严格模式，第二个this会变成undefined

    var a = "a";
    
    function change(){
        "use strict";
        this.a = "b";
    }
    
    console.log(a); //a
    change();
    console.log(a); //uUncaught TypeError: Cannot set property 'foo' of undefined
    
如果在函数前调用了new，this将变成跟全局this无关的一个新值，这个新值亦可称为实例
    
    var a = "a";
    
    function Change(){
        this.a = "b";
    }
    
    console.log(a); //a
    new Change();
    console.log(a); //a
    console.log(new Change().a);    //b
    
### 原型this

你创建的每一个函数都是函数对象。它们会自动获得一个特殊的属性prototype，你可以给这个属性赋值。当你用new的方式调用一个函数的时候，你就能通过this访问你给prototype赋的值了。

    function Test(){
        console.log(this.a);
    }
    
    Test.prototype.a = "a";
    
    var test = new Test();  //a
    console.log(test.a);    //a
    
当你在实例中直接给this赋值时，该值将会覆盖实例原型中的同名属性。实例里面的this是一个特殊的对象。你可以把this想成一种获取prototype的值的一种方式。

    function Test(){}
    
    Test.prototype.a = "a";
    Test.prototype.setA = function(newA){
        this.a = newA;
    }
    
    var test1 = new Test();
    console.log(test1.a);   //a
    
    test1.setA("b");
    console.log(test1.a);   //b
    
如果原型的某个方法里有个嵌套函数，那么该函数并没有继承原型的this

    function Test(){}
    
    Test.prototype.a = "a";
    Test.prototype.fn = function(){
        console.log(this.a);    //a
        
        function inside(){
            console.log(this.a);    //undefined
        }
        inside();
    }
    
    var test = new Test();
    test.fn();

如果手动给inside()函数绑定this


    function Test(){}
    
    Test.prototype.a = "a";
    Test.prototype.fn = function(){
        console.log(this.a);    //a
        
        function inside(){
            console.log(this.a);    //a
        }
        inside.bind(this)();
    }
    
    var test = new Test();
    test.fn();

    