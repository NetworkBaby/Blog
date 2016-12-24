# fetch API

fetch是一种新的W3C标准，用来与远程资源通信，可以替代XMLHttpRequest，提供更加强大、高效的网络请求，目前，chrome已经支持fetch函数。

fetch被定义在BOM的window对象中，该方法返回的是一个promise对象。

例：

    fetch(url).then(function(response){
        return response.json();
    }).then(function(json){
        return json;
    });
    
上面的例子是一个最普通的fetch请求，先构造请求的URL，然后传入fetch()方法，它会立刻返回一个Promise，它会返回一个Response对象，通过该对象的json()方法可以将结果作为JSON对象返回。 response.json()同样会返回一个Promise对象，因此在我们的例子中可以继续链接一个then()方法。

我们还可以配置请求对象，通过Request构造器创建一个新的请求对象。第一个参数是请求的URL，第二个参数是一个选项对象，用于配置请求。请求对象一旦创建了，你便可以将所创建的对象传递给fetch()，用于替换默认的URL。

    var req = new Request(URL, {method: 'GET',cache: 'reload'});
    fetch(req).then(function(response){
        return response.json();
    }).then(function(json){
        return json;
    })

还可以基于原有的Request对象创建一个新的对象，只在原有对象的基础上微微调整即可。例如修改上面的req:

    var post = new Request(req, {method: 'POST'});
    相当于
    var post = new Request(URL, {method: 'POST',cache: 'reload'});
    
每一个Request对象都有一个header属性，在fetch api中对应一个Header对象。通过Header对象，能够修改请求头，而且对于返回的响应，还能轻松的返回有中的各个属性。   

    var headers = new Headers();
    headers.append('Accept', 'application/json');
    var request = new Request(URL, {headers: headers});
    
    fetch(request).then(function(response) {
        console.log(response.headers);
    });