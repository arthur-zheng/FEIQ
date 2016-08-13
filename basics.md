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
