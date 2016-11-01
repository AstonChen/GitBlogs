



### 使用：
* `<script type="text/javascript">...</script>`
* `<script src="xxx.js"></script>`
### var与let：

```javascript
for (var i = 1; i < 3; i++) {
	console.log(i); //1, 2 
}
console.log(i); //3

for (let i = 1; i < 3; i++) {
	console.log(i); //1, 2 
}
console.log(i); //i is not defined...
```
### 数据类型：
* 123; // 整数123
* 0.456; // 浮点数0.456
* 1.2345e3; // 科学计数法表示1.2345x1000，等同于1234.5
* -99; // 负数
* NaN; // NaN表示Not a Number，当无法计算结果时用NaN表示
	* `NaN === NaN;` // false
	* `isNaN(NaN);` // true，测试NaN只能通过`isNaN()`函数。
* Infinity; // Infinity表示无限大，当数值超过了JavaScript的Number所能表示的最大值时，就表示为Infinity
* null; //表示一个“空”的值，它和0以及空字符串''不同，0是一个数值，''表示长度为0的字符串，而null表示“空”。
* undefined; //var a; 此时a就是undefined。JavaScript的设计者希望用null表示一个空的值，而undefined表示值未定义。事实证明，这并没有什么卵用，区分两者的意义不大。大多数情况下，我们都应该用null。undefined仅仅在判断函数参数是否传递的情况下有用。



