# Error

node应用程序的错误一般有一下四种：

- 标准的 JavaScript 错误：
	- <EvalError> : 当调用 eval() 失败时抛出。
	- <SyntaxError> : 当 JavaScript 语法错误时抛出。
	- <RangeError> : 当一个值不在预期范围内时抛出。
	- <ReferenceError> : 当使用未定义的变量时抛出。
	- <TypeError> : 当传入错误类型的参数时抛出。
	- <URIError> : 当一个全局的 URI 处理函数被误用时抛出。
- 由底层操作系的触发的系统错误，例如试图打开一个不存在的文件、试图向一个已关闭的 socket 发送数据等。
- 由应用程序代码触发的用户自定义的错误。
- 断言错误是错误的一个特殊的类，每当 Node.js 检测到一个不应该发生的异常逻辑时会触发。 这类错误通常由 assert 模块触发。

所有 Node.js 引起的 JavaScript 和系统错误都是继承自或实例化自标准的 JavaScript 的 <Error> 类，且保证至少提供类中的可用的属性。

### 一、Error类

Error不表示错误发生的具体情况，会捕捉一个“堆栈跟踪”，详细说明被实例化的Error对象在代码中的位置，并可能提供错误的文字描述。

所有有Node.js产生的错误，包括所有系统的和JavaScript的错误都实例化自或继承自Error类。


#### 实例化：new Error(message)

实例一个error变量，设置error.message属性提供文本信息，如果message是一个对象，则调用message.toString()。error.stack属性表示error在代码中的位置。


### 二、错误类型

#### RangeError类

Error的一个子类，表明一个函数逇一个给定的参数的值不在可接受的集合或范围内；无论是一个数字范围还是给定函数参数的选项的集合。

Node.js会生成并以参数校验的形式立即抛出RangeError实例。

#### ReferenceRrror类

Error的一个子类，表明试图访问一个未定义的变量，这些错误通常表明代码有拼写错误或程序已损坏。

#### SyntaxError类

Error的一个子类，表明程序不是有效的JavaScript代码，这些错误是代码执行的结果产生和传播的。

#### TypeError类

Error的一个子类，表明提供的参数不是一个被允许的类型。

