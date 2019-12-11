# JavaScript深入之闭包

> 对[作用域](https://github.com/winyuan/head-frist-javascript/blob/master/articles/深入系列/JavaScript深入之作用域.md)工作原理有了一定的理解后，就可以开始深入学习闭包了。

## 一、什么是闭包
1. 当函数可以**记住并访问**所在的词法作用域时，就产生了闭包。

2. 举个例子：
```javascript
function foo() {
  var a = 2
  
  function bar() {
    console.log(a)
  }
  
  return bar
}

var baz = foo()
baz() // 2
```
&emsp;&emsp;上例中，我们将 `bar` 引用的函数对象本身当作返回值。此时，虽然 `bar()` 函数**在自己定义的词法作用域以外的地方执行**，但 `bar()` 依然持有对  `foo` 内部作用域的引用，**这个引用就叫作闭包**。  

&emsp;&emsp;拜 `bar()` 所声明的位置所赐，它拥有涵盖 `foo` 内部作用域的闭包，使得该作用域能够一直存活，以供 `bar()` 在之后任何时间进行引用。（否则在 `foo()` 执行后，引用的垃圾回收器会释放不再使用的内存空间）

3. 闭包使得函数可以在其它地方（定义时的词法作用域以外的地方）继续访问定义时的词法作用域。

4. 无论通过何种手段将内部函数**传递**到所在词法作用域以外，它都会持有对原始定义作用域的引用，无论在何处执行这个函数都会使用闭包。  

   举个例子：  
   把内部函数 `baz` 传递给 `bar`，当调用这个内部函数时 （也就是 `fn`），它涵盖的 `foo()` 内部作用域的闭包就可以使用到了，因为它能够访问 `a`。
```javascript
function foo() {
  var a = 2
  
  function baz() {
    console.log(a)
  }
  
  bar(baz)
}

function bar(fn) {
  fn() // 这就是闭包
}

foo() // 2
```
&emsp;&emsp;再举个例子：  
&emsp;&emsp;间接传递函数。

```javascript
var fn

function foo() {
  var a = 2
  
  function baz() {
    console.log(a)
  }
  
  fn = baz // 将 baz 分配给全局变量
}

function bar() {
  fn() // 这就是闭包
}

foo()
bar() // 2
```


## 二、闭包的应用
