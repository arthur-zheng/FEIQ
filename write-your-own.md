#All Others

In a lot of interviews, you will be asked to implement some features.

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