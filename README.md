
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
let arr1 = Array.from(arrayLike); // ['a', 'b', 'c'] 扩展后的数组可以使用 ```arr1

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

设置默认值,   `rest`参数(```变量)名获取函数的多余参数,   箭头函数`this`指向外部对象`this`

```js

var add  = ( a = "a", ```items ) => {
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

var target = {```target, ```source1, ```source2}
target // {a:1, b:2, c:3}

```

>属性遍历

 1.`for```in`

`for```in`循环遍历对象自身的和继承的可枚举属性（不含`Symbol`属性）。

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

```js

export class A {
    //在import的时候需要加大括号
}

export default class B {
    //在import的时候不需要大括号
}

function v1() {```}
export {
  v1 as streamV1, //重命名v1函数的对外接口
  v2 as streamV2,
  v2 as streamLatestVersion
};

```

>import命令

```js

import {firstName, lastName, year} from './profile';

import { lastName as surname } from './profile'; //将输入的变量重命名

import Profile from './profile'

import * as profile from './profile';//模块的整体加载

```

#### Class

>基本语法

```js

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

```

1.类的内部定义方法是不可枚举的,且必须`new`才能使用

2.类的所有实例共享一个原型对象，修改任意实例的`__protp__`会影响所有实例

3.不存在变量提升，实例化前需先定义这个类

4.私有方法 将私有方法的名字命名为一个Symbol值。

```js

class Widget {
  foo (baz) {
    bar.call(this, baz);
  }

  // ```
}

function bar(baz) {
  return this.snaf = baz;
}

```

>Class继承

```js

class Point {
  //父类
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    //tostring方法
  }
}
class ColorPoint extends Point {
  constructor(x, y, color) {
    super(x, y); // 调用父类的constructor(x, y)
    this.color = color;
  }

  toString() {
    return this.color + ' ' + super.toString(); // 调用父类的toString()
  }
}

```

>子类__proto__属性

子类的`__proto__`属性，表示构造函数的继承，总是指向父类<br>

作为一个对象，子类B的原型__proto__属性是父类A

>子类prototype属性的__proto__属性

子类`prototype`属性的`__proto__`属性，表示方法的继承，总是指向父类的prototype属性 <br>

作为一个构造函数，子类B的原型prototype属性是父类的实例

>Object.getPrototypeOf方法可以用来从子类上获取父类。

>super()相当于XXX.prototype.constructor.call(this);

### set数据结构

类似数组，没有重复的值，两个对象总是不相等的

```js

let set = new set([1,2,3,4,4,4])
[...set] //[1,2,3,4]

let set = new set([{},{}])

[...set]// [{},{}]

// 去除数组的重复成员
[...new Set(array)]

```

1.`add(value)`：添加某个值，返回Set结构本身。
2.`delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
3.`has(value)`：返回一个布尔值，表示该值是否为Set的成员。
4.`clear()`：清除所有成员，没有返回值。
5.由于是Iterator对象可以使用遍历器`keys()`，`values()`，`entries()`，`forEach()`

### WeakSet数据结构

1.WeakSet 结构与 Set 类似，也是不重复的值的集合,WeakSet 的成员只能是对象，而不能是其他类型的值

2.WeakSet没有size属性，没有办法遍历它的成员，因为成员都是弱引用，随时可能消失，遍历机制无法保证成员的存在，很可能刚刚遍历结束，成员就取不到了。WeakSet 的一个用处，是储存 DOM 节点，而不用担心这些节点从文档移除时，会引发内存泄漏。

### Map数据结构

>含义

JavaScript 的对象（Object），本质上是键值对的集合（Hash 结构），但是传统上只能用字符串当作键。这给它的使用带来了很大的限制。为了解决这个问题，ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现。如果你需要“键值对”的数据结构，Map 比 Object 更合适。

```js

const m = new Map();
const o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false

对同一个键多次赋值，后面的值将覆盖前面的值。
const map = new Map();

map
.set(1, 'aaa')
.set(1, 'bbb');

map.get(1) // "bbb"

如果读取一个未知的键，则返回undefined。

同样的值的两个实例，在 Map 结构中被视为两个键，内存地址地址不一样
const map = new Map();

const k1 = ['a'];
const k2 = ['a'];

map
.set(k1, 111)
.set(k2, 222);

map.get(k1) // 111
map.get(k2) // 222

```
>Map 和 Set有相同的构造函数，属性和方法，同样可以遍历

> map转Object

```js

function strMapToObj(strMap) {
  let obj = Object.create(null);
  for (let [k,v] of strMap) {
    obj[k] = v;
  }
  return obj;
}

const myMap = new Map()
  .set('yes', true)
  .set('no', false);
strMapToObj(myMap)
// { yes: true, no: false }

```

> Object转map

```js

function objToStrMap(obj) {
  let strMap = new Map();
  for (let k of Object.keys(obj)) {
    strMap.set(k, obj[k]);
  }
  return strMap;
}

objToStrMap({yes: true, no: false})
// Map {"yes" => true, "no" => false}

```

> map转JSON

```js

JSON.stringify(strMapToObj(strMap));//{"yes":true,"no":false}

JSON.stringify([...map])//[[true,7],[{"foo":3},["abc"]]]

```

> map转Object

```js

objToStrMap(JSON.parse(jsonStr));//'{"yes": true, "no": false}'

new Map(JSON.parse(jsonStr))//'[[true,7],[{"foo":3},["abc"]]]'

```

#### WeakMap数据结构

1.WeakMap结构与Map结构类似，但是只接受对象作为键名（null除外），不接受其他类型的值作为键名。
2.它的键名所引用的对象都是弱引用，即垃圾回收机制不将该引用考虑在内。因此，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存。也就是说，一旦不再需要，WeakMap 里面的键名对象和所对应的键值对会自动消失，不用手动删除引用。

以上为ES6常用基础语法
---
