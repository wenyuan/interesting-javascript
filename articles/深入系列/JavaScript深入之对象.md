# JavaScript深入之对象

> 深入了解 JavaScript 中的对象。

## 一、定义对象的方式

1. 声明形式

```javascript
var myObj = {
  key: value
}
```

2. 构造形式

```javascript
var myObj = new Object()
myObj.key = value
```

两种方式生成的对象是一样的，唯一的区别是声明形式中可以添加多个键/值对，构造形式中必须逐个添加属性。

## 二、内置对象

首先需要复习下 JavaScript 中的六种主要类型（语言类型）：

* string
* number
* boolean
* null
* undefined
* object

上述六种类型中，**简单基本类型**（string、number、boolean、null 和 undefined）本身并不是对象，而 `typeof null` 打印得到字符串 `"object"` 只是语言本身的一个 bug。

因此，“~~JavaScript 中万物皆是对象~~” **这句话是错的**。

实际上，JavaScript 有一些对象子类型，通常被称为**内置对象**，有些内置对象的名字看起来和简单基础类型一样。

* String
* Number
* Boolean
* Object
* Function
* Array
* Date
* RegExp
* Error

上述这些内置函数可以使用 `new` 来调用，从而得到一个对应子类型的新对象。举个例子：

```javascript
var strPrimitive = "I am a string"
typeof strPrimitive // "string"
strPrimitive instanceof String // false

var strObject = new String("I am a string")
typeof strObject // "object"
strObject instanceof String // true
```

当然了，在必要时语言会自动把字符串字面量转换成一个 `String` 对象，所以我们不需要显示创建一个对象，也能在这个字面量上执行一些操作，比如：

```javascript
var strPrimitive = "I am a string"
console.log(strPrimitive.length) // 13
console.log(strPrimitive.charAt(3)) // "m"
```

## 三、对象内容

对象的内容是由一些存储在特定命名位置的（任意类型的）值组成的，我们称之为属性。

这些属性一般不会直接存在对象容器内部，存储在对象容器内部的是这些属性的名称，它们就像指针（引用）一样，指向这些值真正的存储位置。

如果要访问对象内部某个属性的值，可以使用 `.` 操作符或者 `[]` 操作符。`.` 语法通常被称为 “属性访问”，`[]` 语法通常被称为  “键访问”。实际上它们访问的是同一个位置，并且会返回相同的值，所以这两个术语是可以互换的。

但使用 `.` 操作符时，要求属性名必须满足标识符的命名规范；使用 `[]` 操作符时，可以接受任意字符串。

```javascript
var myObject = {
  a: 2
}

myObject.a // 2
myObject["a"] // 2
```

数组也是对象，所以虽然每个下标都是整数，但仍然可以给数组添加属性。且当我们通过 `.` 语法或 `[]` 语法给数组添加命名属性后，数组的 `length` 值并不会发生变化。

即便如此，考虑到数组和普通的对象都根据其对应的行为和用途进行了优化，所以**最好只用对象来存储键/值对，只用数组来存储数值下标/值对**。

