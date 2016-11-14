#All Others

In a lot of interviews, you will be asked to implement some features.

### 1. Math.random()
What is it for and how to use it?

`Math.random` returns a number `[0,1)`
```js
// Generate a number between 1-100
// [1,100)

```
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random


### 1. Implement `bind()`
Implement your own `bind()`:
```js
String.prototype.bind = String.prototype.bind ||
function(context) {
    // write your own here
};
const obj = {
    val: 100
};
const test = function() {
    console.log(this.val);
};
const test2 = test.bind(obj);
test2();        // 100
```
One of the answers could be:
```js
String.prototype.bind = String.prototype.bind ||
function(context) {
    const _func = this;
    return function() {
        _func.apply(context, arguments);
    };
}
```