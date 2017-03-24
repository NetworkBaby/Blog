# Events 事件

实例化一个Event对象，如下所示，`eventEmitter.on()`方法用于注册监听器，`eventEmitter.emit()`方法用于触发事件。

	const EventEmitter = require('events');

	class MyEmitter extends EventEmitter {}
	
	const myEmitter = new MyEmitter();

	myEmitter.on('event', () => {
	  console.log('发生了一个事件！');
	});

	myEmitter.emit('event');


### 给监听器传入参数与this

`eventEmitter.emit()`方法允许将任意参数传给监听器函数，当监听器被调用时，this将会指向监听器所附加的`EventEmitter`。

	const myEmitter = new MyEmitter();

	myEmitter.on('event', function(a, b) {
	  console.log(a, b, this);
	  // 打印:
	  //   a b MyEmitter {
	  //     domain: null,
	  //     _events: { event: [Function] },
	  //     _eventsCount: 1,
	  //     _maxListeners: undefined }
	});

	myEmitter.emit('event', 'a', 'b');

不过当使用ES6的箭头函数时，this不指向EventEmitter实例

	const myEmitter = new MyEmitter();

	myEmitter.on('event', (a, b) => {
	  console.log(a, b, this);
	  // 打印: a b {}
	});

	myEmitter.emit('event', 'a', 'b');


### 异步与同步