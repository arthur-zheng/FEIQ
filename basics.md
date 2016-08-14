### Declaration 1
What will be logged?
```js
function test() {
    var a = b = 100;
}
test();
    console.log(b);        // ?
}
```
The answer is 100 instead of `undefined`. Following is what actually happened:
```js
function test() {
    var a = undefined;
    b = 10;
    a = b;
}
...
```
'use strict':
```js
(function() {
    'use strict';
    var a = window.b = 5;
})();
console.log(b);
```


### NaN
What is NaN? What is its type? How can you reliably test if a value is equal to NaN?
NaN 是什么鬼？typeof 的结果是？如果一个变量的值是 NaN，怎么确定？
NaN 是 ‘not a number’ 的缩写，表示 “不是一个数字”，通常会在运算过程中产生：
```js
console.log('abc' / 4);
console.log(4 * 'a');
```
虽然它 “不是一个数字”，但是 NaN 的 typeof 结果却是 number：
console.log(typeof(4 * 'a'));// number
NaN 和任何变量都不相等，包括 NaN 自己：
console.log(NaN === NaN);// false
判断一个变量是不是 NaN 可以用 isNaN() 函数，但是这 并不是一个完美的函数，有些时候用 value !== value 似乎更准确，幸运的是，ES6 已经有 Number.isNaN() 方法，将比 isNaN() 准确的多。

### +-*/
```
let a = 10/3;
a === 3;

console.log(2 + '1');
console.log('2' + 1);

console.log(2 / '1');
console.log(2 - '1');
console.log('2' - 1);

console.log(-'1');
console.log(+'-1');
```

```js
const n = 0.1 + 0.2;
console.log(n === 0.3);
```

