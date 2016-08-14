#Write Your Own
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

### 2. Implement `repeatify()`
Implement `repeatify()`:
```js
String.prototype.repeatify = String.prototype.repeatify ||
function(times) {
    // write your own here
}
// how it works
'Aoo'.repeatify(3);    // 'AooAooAoo'
```
One of the answers could be:
```js
String.prototype.repeatify = String.prototype.repeatify || function(times) {
    // avoid concat for better performance:
    // like: str = ''; str += this;
    const str = [];
    for (var i = 0; i < times; i++) {
        str.push(this);
    }
    return str.join('');
};
```