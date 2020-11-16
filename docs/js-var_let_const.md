---
id: js-var_let_const
title: var, let, const 变量关键字声明
---

## var 关键字

1. 可重复声明
``` javascript
    var a = 1;
    var a = 2;
    console.log(a)
```

2. 在局部作用域声明，不可在全局作用域调用
```javascript
    function fun() {
        var a = 1
        console.log(a) // 1
    }
    console.log(a) // 报错 a is not defined
```

3. 变量提升
``` javascript
    console.log(a); // undefined
    var a;
```

## let 声明

1. 块级作用域, 不能重复声明
``` javascript
if(true) {
    let a = 1
    console.log(a) // 1
}
console.log(a) // a is not defined
let name
let name // 标识符 name 已经声明过

let age = 20
console.log(age) // 20
{
    let age = 18
    console.log(age) // 18
}
```
2. 暂时性死区，在 let 声明之前的执行瞬间被称为 “暂时性死区”
``` javascript
// name 会被提升
console.log(name);
var name; // undefined

console.log(age)
let age // ReferenceError: age is not defined
```
3. 全局声明,使用 let 在全局作用域声明的变量不会称为window对象的属性(var 声明的变量则会)
```javascript
var name = 'xgp'
console.log(window.name) // xgp

let age = 20
console.log(window.age) // undefined 
```
4. for循环中的let 声明
``` javascript
    for(var i = 0; i < 5; i++){
        // 循环逻辑
    }
    console.log(i) // 5

    for(let i = 0; i < 5; i++){
        // 循环逻辑
    }
    console.log(i) // ReferenceError i is not defined

     for(var i = 0; i < 5; i++){
        setTimeout(() => console.log(i), 0)
     } 
     // 5,5,5,5,5
     for(let i = 0; i < 5; i++){
        setTimeout(() => console.log(i), 0)
     } 
     // 0,1,2,3,4
```
var 迭代变量渗透到函数外部，迭代变量保存的是导致循环退出的值: 5。在之后执行超时函数时，所有的 i 都是同一个变量，因为输出的都是不同的变量实例。

而在使用 let 声明迭代变量的时，JavaScript 引擎在后台会为每个迭代循环声明一个新的迭代变量。每个setTimeout引用的都是不同的变量实例，所以输出的是我们期望的值。

## const 声明

1. 声明变量时必须同时初始化变量，且尝试修改const 声明的变量也会报错
``` javascript
    const age = 20
    age = 18 // TypeError: 给常量赋值
    // const 也不允许重复声明
    const name = 'xgp';
    const name = 'wyq'; // SyntaxError

    // const 声明的作用域也是块
    const name = 'xgp';
    if(true) {
        const name = 'wyq';
    }
    console.log(name); // xgp
```
2. const 变量引用的是一个对象，修改这个对象内部的属性并不违反 const 的限制

``` javascript
    const person = {};
    person.name = 'xgp'; 
```

3. const for 循环

for 循环 let , const 声明创建了独立的变量实例(不同的块级作用域)，let 可重新赋值，const 不可重新赋值，所以 const 报 TypeError 给常量赋值。

但是可以在 for-of 和 for-in 中使用，创建独立的变量实例(不同的块级作用域)，没有进行重新赋值操作。
``` javascript
    let i = 0;
    for (const i = 7; i < 5; ++i) {
        console.log(j)
    }
    // 7, 7, 7, 7, 7
    for(const key in {a: 1, b: 2}) {
        console.log(key)
    }
    // a, b
    for(const value of [1,2,3,4,5]) {
        console.log(value)
    }
    // 1, 2, 3, 4, 5
```