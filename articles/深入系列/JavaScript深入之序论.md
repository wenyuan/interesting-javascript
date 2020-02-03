# JavaScript深入之序论

> JavaScript 是什么？

JavaScript 和 ECMAScript 通常都被人们用来表达相同的含义，但 JavaScript 的含义却远比 ECMA-262 中规定的要多得多。（—— 出自红宝书）  

一个完整的 JavaScript 实现应该由下列三个不同的部分组成：
* 核心（ECMAScript）
* 文档对象模型（DOM）
* 浏览器对象模型（BOM）

## ECMAScript

JavaScript 的核心语言特性在 ECMA-262 中是以名为 ECMAScript 的伪语言的形式来定义的。  

ECMAScript 中包含了所有基本的语法、操作符、数据类型以及完成基本的计算任务所必需的对象，但没有对取得输入和产生输出的机制做出规定。