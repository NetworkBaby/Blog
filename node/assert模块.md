# assert模块

## 目录

- assert(value[, message])
- assert.deepEqual(actual, expected[, message])
- assert.deepStrictEqual(actual, expected[, message])
- assert.doesNotThrow(block[, error][, message])
- assert.equal(actual, expected[, message])
- assert.fail(actual, expected, message, operator)
- assert.ifError(value)
- assert.notDeepEqual(actual, expected[, message])
- assert.notDeepStrictEqual(actual, expected[, message])
- assert.notEqual(actual, expected[, message])
- assert.notStrictEqual(actual, expected[, message])
- assert.ok(value[, message])
- assert.strictEqual(actual, expected[, message])
- assert.throws(block[, error][, message])

> assert是nodejs的原生模块，用来断言测试，提供了一些简单的方法。

### 一、assert(value[, message])

等同于assert.ok()，用来判断一个值是否为真。若为真，则会通过该行测试；若为假，则会报错。如果没有第二个参数，则会默认报错"`AssertionError: value == true`"，如果第二个参数存在，则会抛出 "`AssertionError: 不是真值`"

	assert(1);
	assert(true);
	//通过，不会发生什么

	assert(0);
	assert(false);
	//报错，抛出 "AssertionError: 0 == true"
	//报错，抛出 "AssertionError: false == true"

	assert(0, "出错啦");
	//报错，抛出 "AssertionError: 出错啦"


### 二、assert.deepEqual(actual, expected[, message])

相当于"=="，判断是否相等，只比较可枚举的自身属性。message亦是报错信息，默认报错"`AssertionError: actual deepEqual expected`"，自定义"`AssertionError: message`"


### 三、assert.deepStrictEqual(actual, expected[, message])

相当于"==="，判断是否相等，若为对象，还需检查原型是否相等。message亦是报错信息，默认报错"`AssertionError: actual deepStrictEqual expected`"，自定义"`AssertionError: message`"


### 四、assert.doesNotThrow(block[, error][, message])
	
	assert.doesNotThrow(
	  () => {
	    throw new TypeError('错误');
	  },
	  SyntaxError
	);

两个错误相同，抛出`AssertionError: Got unwanted exception (ReferenceError)..[(message)]`；两个错误不相同时，抛出第一个错误，message无用。


### 五、assert.equal(actual, expected[, message])

同二，不深度相等。例如不同对象即使值一样也不等。


### 六、assert.fail(actual, expected, message, operator)

抛出错误`AssertionError: actual operator expected`


### 七、assert.ifError(value)

如果value为真，则抛出value；为假，则通过。


### 八、assert.notDeepEqual(actual, expected[, message])

与deepEqual相反


### 九、assert.notDeepStrictEqual(actual, expected[, message])

与deepStrictEqual相反


### 十、assert.notEqual(actual, expected[, message])

与equal相反，相当于`!=`


### 十一、assert.notStrictEqual(actual, expected[, message])

相当于`!==`


### 十二、assert.ok(value[, message])

相当于`assert.equal(!!value, true, message)`


### 十三、assert.strictEqual(actual, expected[, message])


相当有`===`


### 十四、assert.throws(block[, error][, message])

期望 block 函数抛出错误。

如果指定了 error，error 可以是构造函数、正则表达式、或自定义的验证函数。

如果指定了 message，则当 block 不抛出错误时，message 会作为 AssertionError 的错误信息。

注意，error 不能是一个字符串。 如果第二个参数是一个字符串，则视为省略 error 参数，传入的字符串会被用于 message。




	


	