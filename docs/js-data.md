---
id: js-data
title: JavaScript 数据类型
---

JavaScript数据类型有 Null, Undefined, Boolean, Number, String, Object, Symbol. Symbol(字符)是ECMAScript6新添加的，Object 是复杂数据类型(引用数据类型)，其余都是基本数据类型(原型类型)。

## 数据类型判断

``` jsvascript
console.log('JavaScript 数据类型');
console.log('------------------------------');
console.log('Number 类型');
var a = 1
console.log(typeof a === 'number',"1. typeof 可以判断数字型")
console.log(a instanceof Number, '2. instanceof 不能判断数字类型')
console.log(a.constructor === Number, '3. constructor 可以判断数字类型')
console.log(Object.prototype.toString.call(a) === '[object Number]', '4. Object.prototype.toString.call(a) 可以判断数字')
console.log(Number.isInteger(a), '5. Number.isInteger(a) 可以判断数字')
console.log('------------------------------');
console.log('字符串类型')
a = '1'
console.log(typeof a === 'string', '1. typeof 字符串类型');
console.log(a instanceof String, '2. instanceof 不能判断字符类型')
console.log(a.constructor === String, '3. constructor 可以判断字符串类型')
console.log(Object.prototype.toString.call(a) === '[object String]', '4. Object.prototype.toString.call(a) 可以判断字符串')
console.log('------------------------------');
console.log('数组类型')
a = [1,2,3,4]
console.log(typeof a === 'object', '1. typeof 数组类型 typeof a')
console.log(a instanceof Object, '2. instanceof 对象判断数组也正确 a instanceof Array')
console.log(a.constructor === Array, '3. a.constructor === Array')
console.log(Object.prototype.toString.call(a) === '[object Array]', '4. Object.prototype.toString.call(a)')
console.log(Array.isArray(a), '5. Array.isArray(a)')
console.log('------------------------------');
console.log('布尔类型')
a = true
console.log(typeof a === 'boolean', '1. typeof 可以判断布尔类型');
console.log(a instanceof Boolean, '2. instanceof 不能判断 a instanceof Boolean');
console.log(a.constructor === Boolean, '3. a.constructor 不能判断 a.constructor === Boolean');
console.log(Object.prototype.toString.call(a) === '[object Boolean]', "4. Object.prototype.toString.call(a) === '[object Boolean]' 可以判断");
console.log('------------------------------');
console.log('undefined')
a = undefined
console.log(typeof a === 'undefined', '1. typeof 可以判断未定义类型');
console.log(Object.prototype.toString.call(a) === '[object Undefined]', "2. Object.prototype.toString.call(a) === '[object Undefined]' 可以判断未定义类型");
console.log('------------------------------');
console.log('null')
a = null
console.log(typeof a, '1. typeof 不可判断为 空类型');
console.log(Object.prototype.toString.call(a) ===  '[object Null]', "2. Object.prototype.toString.call(a) === '[object Null]' 可以判断空类型");
if(a === null) {
    console.log('3. a === null 直接判断');
}
console.log('------------------------------');
console.log('对象');
a = {
    name: 1
}
console.log(typeof a === 'object', '1. typeof 可判断 对象类型');
console.log(a instanceof Object, '2. a instanceof Object 可判断对象类型');
console.log(a.constructor === Object, '3. a.constructor === Object 可判断对象类型');
console.log(Object.prototype.toString.call(a) === '[object Object]', "4. Object.prototype.toString.call(a) === '[object Object]' 可以判断对象类型");
console.log('------------------------------');
console.log('函数');
a = function() {}
console.log(typeof a === 'function', '1. typeof 可判断函数类型');
console.log(a instanceof Function, '2. a instanceof Function 可判断函数类型');
console.log(a.constructor === Function, '3. a.constructor === Function 可判断函数类型');
console.log(Object.prototype.toString.call(a) === '[object Function]', "4. Object.prototype.toString.call(a) === '[object Function]' 可判断函数类型");

```

