
#### 前端菜鸡的自我修养

    由阮一峰大神的es6结合实际使用精简出的相关知识点

#### let const

无变量提升，不允许重复声明，只在块级作用域内有效

#### Destructuring(解构)

>数组解构:

```js

let [a, [b], d] = [1, [2, 3], 4]
a// 1
b// 2
d// 4

```

>对象解构:

```js

let { a, b } = {a: "aa", b: "bb"}
a// "aa"
b// "bb"

```

>字符串解构:

```js

const [a, b, c, d, e] = 'hello'
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"

```

>函数参数的解构:

```js

[[1, 2], [3, 4]].map(([a, b]) => a + b);
// [ 3, 7 ]

```
#### 字符串扩展方法

>includes(string,number)

返回布尔值，表示是否找到了参数字符串
>startsWith(string,number)

 返回布尔值，表示参数字符串是否在源字符串的头部
>endsWith(string,number)

 返回布尔值，表示参数字符串是否在源字符串的尾部
>repeat(number)

 表示将原字符串重复n次
>padStart(number,string)

 用于头部补全
>padEnd(number,string)

用于尾部补全

>模板字符串

```js

$('#result').append(`
  There are <b>${basket.count}</b> items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);

```

#### Number扩展

>Number.isNaN()

 用来检查一个值是否为NaN
>Number.isInteger()

 用来判断一个值是否为整数。
>Math.sign()

 参数为正数，返回+1；
 参数为负数，返回-1；
 参数为0，返回0；
 参数为-0，返回-0;
 其他值，返回NaN。
>Math.cbrt()

 方法用于计算一个数的立方根
>Math.sign()

 用来判断一个值的正负，但是如果参数是-0，它会返回-0

>指数运算

```js

2 ** 2 // 4
2 ** 3 // 8

```
#### 数组扩展

>对象转数组

```js

let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};
let arr1 = Array.from(arrayLike); // ['a', 'b', 'c'] 扩展后的数组可以使用 ...arr1

```

>值转数组

```js

Array.of(3, 11, 8) // [3,11,8]

```

>copyWithin()

```js

[1, 2, 3, 4, 5].copyWithin(0, 3, 4) // [4, 2, 3, 4, 5] 将3号位复制到0号位

[1, 2, 3, 4, 5].copyWithin(0, -2, -1) // [4, 2, 3, 4, 5] -2相当于3号位，-1相当于4号位

```

>find()和findIndex()

前者返回第一个符合条件的成员，后者返回第一个符合条件的成员的位置

>fill()

使用给定值，填充一个数组。

```js

['a', 'b', 'c'].fill(7, 1, 2) // ['a', 7, 'c']

```

>entries()，keys()和values() 遍历

```js

for (let index of ['a', 'b'].keys()) {
  console.log(index);
}
// 0
// 1

for (let elem of ['a', 'b'].values()) {
  console.log(elem);
}
// 'a'
// 'b'

for (let [index, elem] of ['a', 'b'].entries()) {
  console.log(index, elem);
}
// 0 "a"
// 1 "b"

```

>includes()

判断数组是否包含给定的值

#### 函数扩展

设置默认值,   `rest`参数(...变量)名获取函数的多余参数,   箭头函数`this`指向外部对象`this`

```js

var add  = ( a = "a", ...items ) => {
	return a;
}

```

尾调用递归优化,只在严格模式适用, 只存在一个调用帧不会出现`stack overflow`错误

```js

function factorial(n, total = 1) {
  if (n === 1) return total;
  return factorial(n - 1, n * total);
}
factorial(5) // 120

```

#### 对象扩展

>简写

```js

var foo = 'bar';
var baz = {
	foo,
	render() { }
};
baz // {foo: "bar", render: function(){}}

```

>属性名表达式

```js

let obj = {
  ['h' + 'ello']() {
    return 'hi';
  }
};
obj.hello() // hi

```

>对象的合并

```js

var target = { a: 1, b: 1 };
var source1 = { b: 2, c: 2 };
var source2 = { c: 3 };

Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}

var target = {...target, ...source1, ...source2}
target // {a:1, b:2, c:3}

```

>属性遍历

 1.`for...in`

`for...in`循环遍历对象自身的和继承的可枚举属性（不含`Symbol`属性）。

 2.`Object.keys(obj)`

`Object.keys`返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含`Symbol`属性）。

 3.`Object.getOwnPropertyNames(obj)`

`Object.getOwnPropertyNames`返回一个数组，包含对象自身的所有属性（不含`Symbol`属性，但是包括不可枚举属性）。

 4.`Object.getOwnPropertySymbols(obj)`

`Object.getOwnPropertySymbols`返回一个数组，包含对象自身的所有`Symbol`属性。

 5.`Reflect.ownKeys(obj)`

`Reflect.ownKeys`返回一个数组，包含对象自身的所有属性，不管属性名是`Symbol`或字符串，也不管是否可枚举。

>Object.keys()，Object.values()，Object.entries()

和数组遍历同理

#### Module 语法

>export命令

规定的是对外的接口

...js

export class A {
    //在import的时候需要加大括号
}

export default class B {
    //在import的时候不需要大括号
}

function v1() {...}
export {
  v1 as streamV1, //重命名v1函数的对外接口
  v2 as streamV2,
  v2 as streamLatestVersion
};

...

>import命令

...js

import {firstName, lastName, year} from './profile';

import { lastName as surname } from './profile'; //将输入的变量重命名

import Profile from './profile'

import * as profile from './profile';//模块的整体加载

...

####class

>基本语法

...js

//定义类
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}

typeof Point // "function"
Point === Point.prototype.constructor // true

...

1.类的内部定义方法是不可枚举的,且必须`new`才能使用

2.类的所有实例共享一个原型对象，修改任意实例的`__protp__`会影响所有实例

3.不存在变量提升，实例化前需先定义这个类

4.私有方法 将私有方法的名字命名为一个Symbol值。

...js

class Widget {
  foo (baz) {
    bar.call(this, baz);
  }

  // ...
}

function bar(baz) {
  return this.snaf = baz;
}

...

>Class继承

















以上为ES6常用基础语法,后续再加
---
