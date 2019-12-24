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

&emsp;&emsp;两种方式生成的对象是一样的，唯一的区别是声明形式中可以添加多个键/值对，构造形式中必须逐个添加属性。


## 二、内置对象
&emsp;&emsp;首先需要复习下 JavaScript 中的六种主要类型（语言类型）：  
&emsp;&emsp;● string  
&emsp;&emsp;● number  
&emsp;&emsp;● boolean  
&emsp;&emsp;● null  
&emsp;&emsp;● undefined  
&emsp;&emsp;● object  

&emsp;&emsp;上述六种类型中，**简单基本类型**（string、number、boolean、null 和 undefined）本身并不是对象，而 `typeof null` 打印得到字符串 `"object"` 只是语言本身的一个 bug。  
&emsp;&emsp;因此，“~~JavaScript 中万物皆是对象~~” **这句话是错的**。  

&emsp;&emsp;实际上，JavaScript 有一些对象子类型，通常被称为**内置对象**，有些内置对象的名字看起来和简单基础类型一样。  
&emsp;&emsp;● String  
&emsp;&emsp;● Number  
&emsp;&emsp;● Boolean  
&emsp;&emsp;● Object  
&emsp;&emsp;● Function  
&emsp;&emsp;● Array  
&emsp;&emsp;● Date  
&emsp;&emsp;● RegExp  
&emsp;&emsp;● Error  

&emsp;&emsp;上述这些内置函数可以使用 `new` 来调用，从而得到一个对应子类型的新对象。举个例子：
```javascript
var strPrimitive = "I am a string"
typeof strPrimitive // "string"
strPrimitive instanceof String // false

var strObject = new String("I am a string")
typeof strObject // "object"
strObject instanceof String // true
```
&emsp;&emsp;当然了，在必要时语言会自动把字符串字面量转换成一个 `String` 对象，所以我们不需要显示创建一个对象，也能在这个字面量上执行一些操作，比如：
```javascript
var strPrimitive = "I am a string"
console.log(strPrimitive.length) // 13
console.log(strPrimitive.charAt(3)) // "m"
```


## 三、对象内容