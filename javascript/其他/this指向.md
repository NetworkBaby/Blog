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



    