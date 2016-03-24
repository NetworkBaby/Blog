# express

## express()

创建一个 Express 应用。express() 是一个由 express 模块导出的入口（top-level）函数。

	var express = require('express');
	var app = express();

### 内置方法

#### express.static(root, [options])

express.static 是 Express 内置的唯一一个中间件。是基于 serve-static 开发的，负责托管 Express 应用内的静态资源。

root 参数指的是静态资源文件所在的根目录。

## Application

The app object conventionally denotes the Express application. Create it by calling the top-level express() function exported by the Express module:

	var express = require('express');
	var app = express();
	
	app.get('/', function(req, res){
	  res.send('hello world');
	});
	
	app.listen(3000);

The app object has methods for

- Routing HTTP requests; see for example, app.METHOD and app.param.
- Configuring middleware; see app.route.
- Rendering HTML views; see app.render.
- Registering a template engine; see app.engine.

It also has settings (properties) that affect how the application behaves; for more information, see Application settings.

### Properties

#### app.locals

The app.locals object is a JavaScript object, and its properties are local variables within the application.

	app.locals.title
	// => 'My App'
	
	app.locals.email
	// => 'me@myapp.com'

Once set, the value of app.locals properties persist throughout the life of the application, in contrast with res.locals properties that are valid only for the lifetime of the request.

You can access local variables in templates rendered within the application. This is useful for providing helper functions to templates, as well as app-level data. Note, however, that you cannot access local variables in middleware.

	app.locals.title = 'My App';
	app.locals.strftime = require('strftime');
	app.locals.email = 'me@myapp.com';

#### app.mountpath

The app.mountpath property is the path pattern(s) on which a sub app was mounted.

A sub app is an instance of express which may be used for handling the request to a route.

	var express = require('express');
	
	var app = express(); // the main app
	var admin = express(); // the sub app
	
	admin.get('/', function (req, res) {
	  console.log(admin.mountpath); // /admin
	  res.send('Admin Homepage');
	})
	
	app.use('/admin', admin); // mount the sub app

It is similar to the baseUrl property of the req object, except req.baseUrl returns the matched URL path, instead of the matched pattern(s).

If a sub-app is mounted on multiple path patterns, app.mountpath returns the list of patterns it is mounted on, as shown in the following example.

	var admin = express();
	
	admin.get('/', function (req, res) {
	  console.log(admin.mountpath); // [ '/adm*n', '/manager' ]
	  res.send('Admin Homepage');
	})
	
	var secret = express();
	secret.get('/', function (req, res) {
	  console.log(secret.mountpath); // /secr*t
	  res.send('Admin Secret');
	});
	
	admin.use('/secr*t', secret); // load the 'secret' router on '/secr*t', on the 'admin' sub app
	app.use(['/adm*n', '/manager'], admin); // load the 'admin' router on '/adm*n' and '/manager', on the parent app

### Events

#### app.on('mount', callback(parent))

The mount event is fired on a sub-app, when it is mounted on a parent app. The parent app is passed to the callback function.

	var admin = express();
	
	admin.on('mount', function (parent) {
	  console.log('Admin Mounted');
	  console.log(parent); // refers to the parent app
	});
	
	admin.get('/', function (req, res) {
	  res.send('Admin Homepage');
	});
	
	app.use('/admin', admin);

### Methods

#### app.all(path, callback [, callback ...])

This method is like the standard app.METHOD() methods, except it matches all HTTP verbs.

It’s useful for mapping “global” logic for specific path prefixes or arbitrary matches. For example, if you put the following at the top of all other route definitions, it requires that all routes from that point on require authentication, and automatically load a user. Keep in mind that these callbacks do not have to act as end-points: loadUser can perform a task, then call next() to continue matching subsequent routes.

	app.all('*', requireAuthentication, loadUser);

Or the equivalent:
	
	app.all('*', requireAuthentication)
	app.all('*', loadUser);

Another example is white-listed “global” functionality. The example is much like before, however it only restricts paths that start with “/api”:

	app.all('/api/*', requireAuthentication);


#### app.delete(path, callback [, callback ...])

Routes HTTP DELETE requests to the specified path with the specified callback functions. For more information, see the routing guide.

You can provide multiple callback functions that behave just like middleware, except these callbacks can invoke next('route') to bypass the remaining route callback(s). You can use this mechanism to impose pre-conditions on a route, then pass control to subsequent routes if there’s no reason to proceed with the current route.
	
	app.delete('/', function (req, res) {
	  res.send('DELETE request to homepage');
	});
	


