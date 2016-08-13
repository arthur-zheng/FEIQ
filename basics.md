### Declaration
```js
function test() {
    var a = b = 100;
}
test();
console.log(b);        // ?
}
```
This is what actually happened:
```js
function test() {
    var a = undefined;
    b = 10;
    a = b;
}
...
```
