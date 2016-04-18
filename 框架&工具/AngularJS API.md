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



























