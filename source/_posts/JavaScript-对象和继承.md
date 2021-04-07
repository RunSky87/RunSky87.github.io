---
title: JavaScript-对象和继承
date: 2021-04-07 21:31:06
tags: JavaScript
---

### 数据属性
- Configurable：表示能否通过delete 删除属性，能否修改属性的特性，或者能否把属性修改为访问器属性。默认为true。
- Enumerable：表示能否通过for-in 循环返回属性。默认为true。
- Writable：表示能否修改属性的值。默认为true。
- Value：包含这个属性的数据值。默认为undefined。

默认情况,如下所示，person.name 的 value 为 test-name,默认可遍历，可修改，可删除。
```js
var person = {
  name: "test-name"
};
```

### 设置属性的特性
#### Object.defineProperty()方法
这个方法接收三个参数：属性所在的对象、属性的名字和一个描述符对象。其中，描述符（descriptor）对象的属性必须是：configurable、enumerable、writable 和value。设置其中的一或多个值，可以修改对应的特性值。以设置不可修改为例：
```js
var person = {};
Object.defineProperty(person, "name", {
  writable: false,
  value: "Nicholas"
});
alert(person.name); //"Nicholas"
person.name = "Greg";
alert(person.name); //"Nicholas"
```

### 访问器属性的特性
- Configurable：表示能否通过delete 删除属性，能否修改属性的特性，或者能否把属性修改为数据属性。默认为true。
- Enumerable：表示能否通过for-in 循环返回属性，默认为true。
- Get：在读取属性时调用的函数。默认值为undefined。
- Set：在写入属性时调用的函数。默认值为undefined。

### 定义访问器属性
#### Object.defineProperty()方法
```js
var book = {
  // 下划线是一种常用的记号，用于表示只能通过对象方法访问的属性  
  _year: 2004,
  edition: 1
};

Object.defineProperty(book, "year", {
  get: function(){
    return this._year;
  },
  set: function(newValue){
    if (newValue > 2004) {
      this._year = newValue;
      this.edition += newValue - 2004;
    }
  }
});

book.year = 2005;
alert(book.edition); //2
```

### 定义多个属性
#### Object.defineProperties()方法
利用这个方法可以通过描述符一次定义多个属性。这个方法接收两个对象参数：第一个对象是要添加和修改其属性的对象，第二个对象的属性与第一个对象中要添加或修改的属性一一对应。例如：
```js
var book = {};
Object.defineProperties(book, {
  _year: {
    value: 2004
  },
  
  edition: {
    value: 1
  },

  year: {
    get: function(){
      return this._year;
    },

    set: function(newValue){
      if (newValue > 2004) {
        this._year = newValue;
        this.edition += newValue - 2004;
      }
    } 
  }
});
```

### 查看属性的特性
#### Object.getOwnPropertyDescriptor()方法
这个方法接收两个参数：属性所在的对象和要读取其描述符的属性名称。返回值是一个对象，如果是访问器属性，这个对象的属性有configurable、enumerable、get 和set；如果是数据属性，这个对象的属性有configurable、enumerable、writable 和value。例如：
```js
var book = {};

Object.defineProperties(book, {
  _year: {
    value: 2004
  },

  edition: {
    value: 1
  },

  year: {
    get: function(){
      return this._year;
    },

    set: function(newValue){
      if (newValue > 2004) {
        this._year = newValue;
        this.edition += newValue - 2004;
      }
    }
  }
});

var descriptor = Object.getOwnPropertyDescriptor(book, "_year");
// {value: 2004, writable: false, enumerable: false, configurable: false}
alert(descriptor.value); //2004
alert(descriptor.configurable); //false
alert(typeof descriptor.get); //"undefined"

var descriptor = Object.getOwnPropertyDescriptor(book, "year");
// {enumerable: false, configurable: false, get: ƒ, set: ƒ}
alert(descriptor.value); //undefined
alert(descriptor.enumerable); //false
alert(typeof descriptor.get); //"function"
```
