---
title: JavaScript-常用的引用类型
date: 2021-03-19 12:48:53
tags: JavaScript
---

### 方括号语法的优点是啥
方括号语法的主要优点是可以通过变量来访问属性
```js
var person = {name:"zhang-san"}
var propertyName = "name";
console.log(person[propertyName]); // zhang-san
```
如果属性名中包含会导致语法错误的字符，或者属性名使用的是关键字或保留字，也可以使用方括号表示法
```js
var person = {"my name":"zhang-san"}
console.log(person["my name"]); // zhang-san
```

### 怎么确定某个对象是不是数组
对于一个网页，或者一个全局作用域而言，使用instanceof 操作符
```js
if (value instanceof Array){
  //对数组执行某些操作
}
```
instanceof 操作符的问题在于，它假定只有一个全局执行环境。如果网页中包含多个框架，那实际上就存在两个以上不同的全局执行环境，从而存在两个以上不同版本的Array 构造函数。如果你从一个框架向另一个框架传入一个数组，那么传入的数组与在第二个框架中原生创建的数组分别具有各自不同的构造函数。
为了解决这个问题，ECMAScript 5 新增了Array.isArray()方法
```js
if (Array.isArray(value)){
  //对数组执行某些操作
}
```

### alert 为什么可以输出数组
由于alert()要接收字符串参数，所以它会在后台调用toString()方法，由此会得到与直接调用toString()方法相同的结果。

<!-- more -->

### 常用数组方法
#### 基础操作
```js
var colors = new Array();

// 入栈 - push
var count = colors.push("red", "green"); // 在后面加入，可接收任意数量参数
console.log(count); // 返回数组长度

// 出栈 - pop
var item = colors.pop(); // 移除最后一项
console.log(item); // 返回被移除的项

// 入队 - unshift
var count = colors.unshift("red", "green"); // 在前面加入，可接收任意数量参数
console.log(count); // 返回数组长度

// 出队 - shift
var item = colors.shift(); // 移除第一项
console.log(item); // 返回被移除的项

----------------------------

var values = [3, 1, 4, 5, 2];

// 数组反转 - reverse
values.reverse(); // 数组反转
console.log(values); // [2,5,4,1,3]

// 数组排序 - soft
values.sort(); // 默认从小到大排序
console.log(values); // [1,2,3,4,5]

-----------------------------
indexOf()和lastIndexOf()。这两个方法都接收两个参数：要查找的项和（可选的）表示查找起点位置的索引

var numbers = [1,2,3,4,5,4,3,2,1];

// 查找第一次出现的位置
numbers.indexOf(4); // 3
numbers.indexOf(4, 4); // 5
numbers.indexOf(8); // -1

// 查找最后一次出现的位置
numbers.lastIndexOf(4); // 5
numbers.lastIndexOf(4, 4); // 3
numbers.lastIndexOf(8); // -1
```

#### sort() 是如何进行排序的
在默认情况下，sort()方法按升序排列数组项——即最小的值位于最前面，最大的值排在最后面。
为了实现排序，sort()方法会调用每个数组项的toString()转型方法，然后比较得到的字符串，以确定如何排序。即使数组中的每一项都是数值，sort()方法比较的也是字符串，
数值5 虽然小于10，但在进行字符串比较时，"10"则位于"5"的前面，如下所示，使用比较函数可以解决此问题：
```js
var values = [0, 1, 5, 10, 15];
values.sort(); // [0,1,10,15,5]

values.sort((a,b)=>a-b) // [0, 1, 5, 10, 15]
values.sort((a,b)=>b-a) // [15,10,5,1,0]
```
根据某属性排序
```js
var values = [
    {number : 3},
    {number : 6},
    {number : 5}
    ]

function createComparisonFunction(propertyName) {
  return function(object1, object2){
    var value1 = object1[propertyName];
    var value2 = object2[propertyName];
    return value1 - value2;
  };
}

values.sort(createComparisonFunction('number'))

console.dir(values)
> Array(3)
0: {number: 3}
1: {number: 5}
2: {number: 6}
length: 3
```

#### concat() 方法实现拷贝和拼接
其中，concat()方法可以基于当前数组中的所有项创建一个新数组。
具体来说，这个方法会先创建当前数组一个副本，然后将接收到的参数添加到这个副本的末尾，最后返回新构建的数组。在没有给concat()方法传递参数的情况下，它只是复制当前数组并返回副本。如果传递给concat()方法的是一或多个数组，则该方法会将这些数组中的每一项都添加到结果数组中。
```js
var colors = ["red", "green", "blue"];
var colors2 = colors.concat(); // 拷贝，新开一块内存
var colors3 = colors; // 指向同一个内存地址
var colors4 = colors.concat("yellow", ["black", "brown"]); // 可以接收任意数量参数
```

#### slice() 方法抽取部分数组
能够基于当前数组中的一或多个项创建一个新数组。slice()方法可以接受一或两个参数，即要返回项的起始和结束位置。在只有一个参数的情况下，slice()方法返回从该参数指定位置开始到当前数组末尾的所有项。
如果有两个参数，该方法返回起始和结束位置之间的项(但不包括结束位置的项)
如果slice()方法的参数中有一个负数，则用数组长度加上该数来确定相应的位置
第二个参数如果小于第一个参数，则返回空数组

```js
var colors = ["red", "green", "blue", "yellow", "purple"];
var colors2 = colors.slice(); // ["red", "green", "blue", "yellow", "purple"]
var colors3 = colors.slice(0); // ["red", "green", "blue", "yellow", "purple"]
var colors4 = colors.slice(-3,-1); // ["blue", "yellow"]
```

#### splice()方法用于替换
splice()的主要用途是向数组的中部插入项，但使用这种方法的方式则有如下3 种。
- 删除：可以删除任意数量的项，只需指定2 个参数：要删除的第一项的位置和要删除的项数。例如，splice(0,2)会删除数组中的前两项。
- 插入：可以向指定位置插入任意数量的项，只需提供3 个参数：起始位置、0（要删除的项数）和要插入的项。如果要插入多个项，可以再传入第四、第五，以至任意多个项。例如，splice(2,0,"red","green")会从当前数组的位置2 开始插入字符串"red"和"green"。
- 替换：可以向指定位置插入任意数量的项，且同时删除任意数量的项，只需指定3 个参数：起始位置、要删除的项数和要插入的任意数量的项。插入的项数不必与删除的项数相等。例如，splice (2,1,"red","green")会删除当前数组位置2 的项，然后再从位置2 开始插入字符串"red"和"green"。

splice()方法始终都会返回一个数组，该数组中包含从原始数组中删除的项

#### 常用的迭代方法和归并方法
下列方法都不会修改数组中的值，只是返回新的数组
- every()：对数组中的每一项运行给定函数，如果该函数对每一项都返回true，则返回true。
- filter()：对数组中的每一项运行给定函数，返回该函数会返回true 的项组成的数组。
- forEach()：对数组中的每一项运行给定函数。这个方法没有返回值。
- map()：对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。
- some()：对数组中的每一项运行给定函数，如果该函数对任一项返回true，则返回true。
- reduce()：接收4 个参数：前一个值、当前值、项的索引和数组对象。这个函数返回的任何值都会作为第一个参数自动传给下一项。适用于累加等操作。
- reduceRight()：功能与 reduce() 方法相同，不过是从数组的最后一项开始，向前遍历到第一项。


### 正则 exec() 方法
```js
var co = "red,green,blue,yellow,purple"
var a = /r/g

a.exec(co)
> ["r", index: 0, input: "red,green,blue,yellow,purple", groups: undefined]
a.exec(co)
> ["r", index: 5, input: "red,green,blue,yellow,purple", groups: undefined]
a.exec(co)
> ["r", index: 24, input: "red,green,blue,yellow,purple", groups: undefined]
a.exec(co)
> null
```

### 正则 test() 方法
它接受一个字符串参数。在模式与该参数匹配的情况下返回true；否则，返回false。在只想知道目标字符串与某个模式是否匹配，但不需要知道其文本内容的情况下，使用这个方法非常方便。因此，test()方法经常被用在if 语句中，如下面的例子所示。
```js
var text = "000-00-0000";
var pattern = /\d{3}-\d{2}-\d{4}/;
if (pattern.test(text)){
  console.log("匹配成功");
}
```

### 怎么理解函数实际上是对象
每个函数都是Function 类型的实例，而且都与其他引用类型一样具有属性和方法。
```js
var funcA = function(){console.log('funcA')};
funcA.funcB = function(){console.log('funcB')};
funcA.test = 12312;

funcA() // 'funcA'
funcA.test // 12312
funcA.funcB() // 'funcB'
```



