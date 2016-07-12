# AngularJS API

## ng

### function

#### angular.fromJson

字符串转JSON格式

	angular.fromJson("{\"firstName\":\"fox\",\"lastName\":\"zhang\"}");

#### angular.identity

函数返回本身的第一个参数。这个函数一般用于函数风格。

	function transformer(transformationFn, value) {
	  return (transformationFn || angular.identity)(value);
	};

#### angular.injector
	
创建一个injector对象, 调用injector对象的方法可以获得angular的service, 或者用来做依赖注入.

#### angular.isArray

判断一个数据是否是数组

#### angular.isDate

判断给定的对象是否为日期类型

#### angular.isDefined

判断一个数据是否是defined类型

#### angular.isElement

判断对象是否是DOM元素（或者jQuery元素）

#### angular.isFunction

判断对象是否函数

#### angular.isNumber

判断对象是否数字

#### angular.isObject

判断对象是否对象

#### angular.isString

判断对象是否字符串类型

#### angular.isUndefined

判断对象是否是undefined类型

#### angular.lowercase

全部字符转为小写

#### angular.module

	angular.module("app", [ "controls", "data"])

#### angular.noop

angular.noop is an empty function that can be used as a placeholder when you need to pass some function as a param.

当你需要一些函数作为参数时，可以作为一个空函数占位。

#### angular.reloadWithDebugInfo

重新加载应用并打开调试模式

#### angular.toJson

将字符串转换成json格式

#### angular.uppercase

全部字符转为大写

### directive

#### a

a标签，修改了a标签的默认事件，故当a标签链接为空时阻止了默认事件

#### form

ng-form或者form，已被angular改写。ng-model双向绑定input等元素，myForm.personEmail.$valid判断是否合法，myForm.personEmail.$error判断具体错误，ng-disabled="myForm.$invalid"判断表单是否可以提交，ng-submit="save()"提交执行的函数。

#### input

属性：ng-model/name/required/ng-required/ng-minlength/ng-maxlength/ng-pattern/ng-change/ng-trim/ng-true-value/ng-false-value/ng-pattern

#### ng-app

angular应用，管理页面

#### ng-bind

绑定数据在页面上

#### ng-bind-html

绑定html元素在页面上

#### ng-bind-template

绑定模板

#### ng-blur

失去焦点后执行

#### ng-change

改变内容后执行

#### ng-checked

选中后执行

#### ng-class

	ng-class {'selected': isSelected, 'car': isCar}"

#### ng-class-even

偶数个应用此类

#### ng-class-odd

基数个应用此类

#### ng-click

点击事件

#### ng-cloak

防止绑定的模板闪烁

#### ng-controller

控制器

#### ng-copy

深拷贝

#### ng-dblclick

双击事件

#### ng-disabled

控制失效状态

#### ng-focus

获得焦点

#### ng-form

#### ng-hide

隐藏

#### ng-href

链接中有参数时用

#### ng-if

通过删除或新增节点

#### ng-include

引入html文件

#### ng-init

可以初始化变量、对象、数组

#### ng-keydown

键盘按下事件

#### ng-keypress

键盘按下事件

#### ng-keyup

键盘松开事件

#### ng-list

绑定在input，将字符串转换为数组，用逗号隔开

#### ng-model

实现双向绑定

#### ng-model-options

规定什么时候刷新数据

#### ng-mousedown

鼠标按下事件

#### ng-mouseenter

鼠标移入事件

#### ng-mouseleave

鼠标移出事件

#### ng-mousemove

鼠标移动事件

#### ng-mouseup

鼠标松开事件

#### ng-non-bindable

对表达式不执行，绑定无效

#### ng-open

显示可见或者不可见

#### ng-paste

粘贴

#### ng-pluralize

#### ng-readonly

只读状态

#### ng-repeat

循环数组或者对象

#### ng-selected

选中

#### ng-show

显示

#### ng-src

路径，可以增加表达式

#### ng-style

样式改变

#### ng-submit

提交前执行

#### ng-switch

可以根据ng-switch-when、ng-default选择

#### ng-value

设置input/select的value值






















