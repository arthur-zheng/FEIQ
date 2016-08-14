
###Keys are strings

What is the output out of the following code? Explain your answer.
```js
vara={},
b={key:'b'},
c={key:'c'};
a[b]=123;
a[c]=456;
console.log(a[b]);
```
一道有趣的题目，答案是 456。
我们知道，Javascript 中对象的 key 值，一定会是一个 string 值，如果不是，则会隐式地进行转换。当执行到 a[b]=123] 时，b 并不是一个 string 值，将 b 执行 toString() 方法转换（得到 “[object Object]“），a[c] 也是相同道理。所以代码其实可以看做这样执行：
```js
vara={},
b={key:'b'},
c={key:'c'};
// a[b]=123;
a["[object Object]"]=123;
// a[c]=456;
a["[object Object]"]=456;
console.log(a["[object Object]"]);
这样就一目了然了。
```