# sass简单语法

### 使用

	sass test.scss test.css

SASS提供四个编译风格的选项:

- nested：嵌套缩进的css代码，它是默认值。
- expanded：没有缩进的、扩展的css代码。
- compact：简洁格式的css代码。
- compressed：压缩后的css代码。


	sass --style compressed test.sass test.css

你也可以让SASS监听某个文件或目录，一旦源文件有变动，就自动生成编译后的版本。

	// watch a file
	sass --watch input.scss:output.css
	// watch a directory
	sass --watch app/sass:public/stylesheets

#### 变量

SASS允许使用变量，所有变量以$开头。

	$blue : #1875e7;　
	div {
		color : $blue;
	}

如果变量需要镶嵌在字符串之中，就必须需要写在#{ }之中。

	$side : left;
	.rounded {
		border-#{$side}-radius: 5px;
	}

#### 计算功能

SASS允许在代码中使用算式：

	body {
		margin: (14px/2);
		top: 50px + 100px;
		right: $var * 10%;
	}

