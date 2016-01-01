# webpack实战

from:[http://www.cnblogs.com/tugenhua0707/p/4793265.html#_labelTop](http://www.cnblogs.com/tugenhua0707/p/4793265.html#_labelTop)

目录：

- 一：什么是webpack? 他有什么优点？
- 二：如何安装和配置
- 三：理解webpack加载器
- 四：理解less-loader加载器的使用
- 五：理解babel-loader加载器的含义
- 六：了解下webpack的几个命令
- 七：webpack对多个模块依赖进行打包
- 八：如何独立打包成样式文件
- 九：如何打包成多个资源文件
- 十：关于对图片的打包
- 十一：React开发神器：react-hot-loader

### 一：什么是webpack? 他有什么优点？

首先对于很多刚接触webpack人来说，肯定会问webpack是什么？它有什么优点？我们为什么要使用它？带着这些问题，我们来总结下如下：

**Webpack是前端一个工具，可以让各个模块进行加载，预处理，再进行打包，它能有Grunt或Gulp所有基本功能。**优点如下：

- 支持commonJS和AMD模块。
- 支持很多模块加载器的调用，可以使模块加载器灵活定制，比如babel-loader加载器，该加载器能使我们使用ES6的语法来编写代码。
- 可以通过配置打包成多个文件，有效的利用浏览器的缓存功能提升性能。
- 使用模块加载器，可以支持sass，less等处理器进行打包且支持静态资源样式及图片进行打包。
- 更多等等。。。带着这些问题我们慢慢来学习webpack。

### 二：如何安装和配置

首先我的项目目录结构是：文件名叫webpack，里面只有一个main.html，代码如下：

	<!doctype html>
	<html lang="en">
	 <head>
	  <meta charset="UTF-8">
	  <title>Document</title>
	  <script src="src/react.min.js"></script>
	 </head>
	 <body>
	    <div id="content"></div>
	    <script src="build/build.js"></script>
	 </body>
	</html>

还有一个文件夹src，该文件夹存放了二个js文件；react.min.js源文件和main.js文件，main.js源码如下：

	/* 内容区模块代码 */
	var ContentMode = React.createClass({
	        render: function(){
	            return (
	                <div className="ContentMode">
	                    <div class="contents">{this.props.contents}</div>
	                    {this.props.children}
	                </div>
	            )
	        }
	});
	/* 页面div封装 上面三个模块 */
	var Page = React.createClass({
	    render: function(){
	        return (
	            <div className="homepage">
	                <ContentMode  contents ="longen">this is one comment</ContentMode >
	                <ContentMode  contents ="longen2">this is two comment</ContentMode >
	            </div>
	            )
	        }
	});
	/* 初始化到content容器内 */
	React.render(
	       React.createElement(Page,null),document.getElementById("content")
	);

该代码是React.js代码，是react.js入门学习一中的代码复制过来的，为了演示；

**安装步骤如下：**

1.生成package.json文件

首先我们需要在根目录下生成package.json文件，需要进入项目文件内根目录下执行如下命令：`npm init`

![webpack] (../images/16.1.1img11.png)

如上通过一问一答的方式后会在根目录下生成package.json文件，如下所示：

![webpack] (../images/16.1.1img12.png)

2 . 通过全局安装webpack

执行命令如下：`npm install -g webpack` 如下所示：

![webpack] (../images/16.1.1img13.png)

在c盘下会生成`node_modules`文件夹中会包含webpack，此时此刻我们可以使用webpack命令了；

3. 配置webpack

每个目录下都必须有一个`webpack.config.js`，它的作用就好比Gulpfile.js、或者 Gruntfile.js，就是一个项目配置，告诉webpack需要做什么。

如下是我的webpack.config.js代码如下：

	module.exports = {
	  entry: "./src/main.js",
	  output: {
	    filename: "build/build.js"
	  },
	  module: {
	    loaders: [
	       //.css 文件使用 style-loader 和 css-loader 来处理
	      { test: /\.css$/, loader: "style!css" },
	      //.js 文件使用 jsx-loader 来编译处理
	      { test: /\.js$/,    loader: "jsx-loader" }
	    ]
	  },
	  resolve: {
	    extensions: ['', '.js', '.jsx']
	  },
	  plugins: []
	};

`entry`：是页面中的入口文件，比如我这边的入口文件时main.js

`output`: 是指页面通过webpack打包后生成的目标文件放在什么地方去，我这边是在根目录下生成build文件夹，该文件夹内有一个build.js文件；

`resolve`: 定义了解析模块路径时的配置，常用的就是extensions; 可以用来指定模块的后缀，这样在引入模块时就不需要写后缀，会自动补全。

`plugins`: 定义了需要使用的插件，比如commonsPlugin在打包多个入口文件时会提取公用的部分，生成common.js;

`module.loaders`：是文件的加载器，比如我们之前react需要在页面中引入jsx的js源码到页面上来，然后使用该语法，但是通过webpack打包后就不需要再引入JSXTransformer.js；看到上面的加载器；比如jsx-loader加载器就是代表JSXTransformer.js的，还有style-loader和css-loader加载器；因此在使用之前我们需要通过命令把它引入到项目上来；因此需要如下命令生成下；

`jsx-loader`加载器 `npm install jsx-loader --save-dev` 如下：

![webpack] (../images/16.1.1img14.png)

`Style-loader`加载器 `npm install style-loader --save-dev` 如下：

![webpack] (../images/16.1.1img15.png)

`css-loader` 加载器 `npm install css-loader --save-dev` 如下：

![webpack] (../images/16.1.1img16.png)

局部安装webpack 执行命令：`npm install webpack --save-dev`

![webpack] (../images/16.1.1img17.png)

我们这边干脆把gulp的全局安装和在项目中局部安装也安装下，稍后有用~

Gulp全局安装 npm install -g gulp 如下：

![webpack] (../images/16.1.1img18.png)

在项目文件内，gulp局部安装 使用命令 `npm install gulp --save-dev` 如下所示：

![webpack] (../images/16.1.1img19.png)

因此在我们文件夹node_modules下生成文件如下：

![webpack] (../images/16.1.1img20.png)

现在我们来执行命令 webpack; 如下所示：

![webpack] (../images/16.1.1img21.png)

即可在根目录下生成一个build文件夹中build.js 如下所示：

![webpack] (../images/16.1.1img22.png)

我们还可以使用如下命令：`webpack --display-error-details` 命令执行，这样的话方便出错的时候可以查看更详尽的信息；比如如下：

![webpack] (../images/16.1.1img23.png)

现在我们再来刷新下页面；看到如下：

![webpack] (../images/16.1.1img24.png)

可以看到页面渲染出来了，我们接着来看看页面中的请求：

![webpack] (../images/16.1.1img25.png)

可以看到只有一个文件react.min.js的源文件和build.js 我们刚刚生成的build.js文件了，因此我们通过webpack进行打包后，我们现在就不再需要和以前一样引入JSXTransformer.js了。我们还可以看看build.js内生成了那些js，这里就不贴代码了，自己可以看看了~

上面是使用webpack打包；现在我们再来看看使用第二种方案来打包~

**使用gulp来进行打包**

我们知道使用gulp来打包的话，那么我们需要在根目录下需要新建 Gulpfile.js；

因此我们这边Gulpfile.js的源码如下：

	var gulp = require('gulp');
	var webpack = require("gulp-webpack");
	var webpackConfig = require("./webpack.config.js");
	
	gulp.task('webpack', function () {
	    var myConfig = Object.create(webpackConfig);
	    return gulp
	        .src('./src/main.js')
	        .pipe(webpack(myConfig))
	        .pipe(gulp.dest('./build'));
	});
	
	// 注册缺省任务
	gulp.task('default', ['webpack']);

然后webpack.config.js代码变为如下：

	module.exports = {
	  entry: "./src/main.js",
	  output: {
	    filename: "build.js"
	  },
	  module: {
	    loaders: [
	       //.css 文件使用 style-loader 和 css-loader 来处理
	      { test: /\.css$/, loader: "style!css" },
	      //.js 文件使用 jsx-loader 来编译处理
	      { test: /\.js$/,    loader: "jsx-loader" }
	    ]
	  },
	  resolve: {
	    extensions: ['', '.js', '.jsx']
	  },
	  plugins: []
	};

即可，然后再在命令行中输入gulp即可生成build/build.js了，如下所示：

![webpack] (../images/16.1.1img26.png)

Github上的代码如下： [https://github.com/tugenhua0707/webpack/](https://github.com/tugenhua0707/webpack/)  自己可以把压缩包下载下来运行下即可。

### 三：理解webpack加载器





















