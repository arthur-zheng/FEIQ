#Event Loop Questions
To help understand Javascript's Event Loop System. I recommend you to read this book: _Secrets of Javascript Ninja_
https://www.manning.com/books/secrets-of-the-javascript-ninja

###1. `setTimeout()`

```js
function test() {
    console.log(1);
    setTimeout(function() {
        console.log(2);
    }, 1000);
    setTimeout(function() {
        console.log(3);
    }, 0);
    console.log(4);
}
test();
```
Answer is: `1, 4, 3, 2`. Whatever inside setTimeout will be asigned into the end of event loop. So after `1` was logged, `4` will be the next. Then event loop moves to the `0` and `3`.

```js
function test() {
    for (let i = 0; i < 5; i++) {    // we used let in here
        setTimeout(function() {
            console.log(i);
        }, 1000);
    }
}
test();
```
As we know from chapter closure, a new i was created each loop. Thus the answer is `0, 1, 2, 3, 4`. This is exactly what we expect from event loop.

###2. `setInterval()`
What's the difference between the `setTimeout` and `setInternal`?
```js
// Taobao Interview Question
// Author: oklai@zhihu
setTimeout(function(){
    /* ... */
    setTimeout(arguments.callee, 10);
}, 10);
setInterval(function(){ 
    /*... */
}, 10);
```


###References:
1. _5 More JavaScript Interview Exercises_
https://www.sitepoint.com/5-javascript-interview-exercises/
2. 有哪些经典的 Web 前端或者 JavaScript 面试笔试题？https://www.zhihu.com/question/19841848