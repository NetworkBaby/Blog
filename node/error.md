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

