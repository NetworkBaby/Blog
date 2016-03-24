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