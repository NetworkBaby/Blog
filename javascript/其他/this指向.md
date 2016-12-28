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

你可以用bind来代替任何一个函数或者方法的this，即便它没有赋值给实例的初始prototype
    
    function Test(){}
    
    Test.prototype.a = "a";
    
    function log(){
        console.log(this.a);
    }
    
    var test = new Test();
    log.bind(test)();   //a
    log.apply(test);    //a
    log.call(test);     //a
    log();              //undefined
    
### 对象this

在一个对象中，如果有一个属性为函数，那么在函数里面可以用this引用该对象的其他属性。

    var obj = {
        a: "a",
        fn: function(){
            console.log(this.a);
        }
    }
    
    obj.fn();   //a
    
当使用以下方式时，this不会越出当前对象，只有相同直接父元素的属性才能通过this共享变量

    var obj = {
        a: "a",
        fn: {
            inside: function(){
                console.log(this);
            }
        }
    }
    
    obj.fn.inside();    //undefined
    
### DOM 对象this

在一个事件处理函数中，this始终指代这个处理函数所绑定的DOM节点中。

    function Listener(){
        document.querySelector('#test').addEventListener('click', this.handerClick);
    }
    
    Listener.prototype.handerClick = function(){
        console.log(this);
    }
    
    var listener = new Listener();
    document.quertSelector('#test').click();    //id为test的dom节点
    
还可以手动切换上下文

    function Listener(){
        document.querySelector('#test').addEventListener('click', this.handerClick.bind(this));
    }
    
    Listener.prototype.handerClick = function(){
        console.log(this);
    }
    
    var listener = new Listener();
    document.quertSelector('#test').click();    //Listener {handleClick: function}
    
### HTML this

html节点中放置的javascript，this指向了这个元素

    <div id="test" onclick="console.log(this);"></div>
    <script>
        document.querySelector('#test').click();    //<div id="test"></div>
    </script>


