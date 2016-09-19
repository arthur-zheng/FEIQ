### Declaration
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
##### How about using 'use strict'?
```js
(function() {
    'use strict';
    var a = window.b = 5;
})();
console.log(b);
```


### NaN
##### 1. When is NaN be produced?
```js
// Only '+' sign will try to do some concat.
// Other operations ( / * - ) will produce NaN when number and string are mixed.
console.log('abc'/4);
console.log(4*'a');

// How to check NaN:
Number.isNaN(NaN);    // true, only if is NaN

// Be careful of pitfalls from isNaN() (not Number.isNaN()):
isNaN({});         // true
isNaN('a');        // true
typeof(NaN);       // "number"
NaN === NaN        // false
```

### + - * /
##### 1. What will be logged?
```js
let a = 10/3;
a === 3;

console.log(2 + '1');            // 21  
console.log('2' + 1);            // 21

console.log(2 / '1');            // 2
console.log(2 - '1');            // 1
console.log('2' - 1);            // 1

console.log('2' - 'a');          // NaN

console.log(-'1');               // -1
console.log(+'-1');              // -1
```
##### 2. Does it equal? Why?
```js
const n = 0.1 + 0.2;
console.log(n === 0.3);
```

### Check Types

##### 1. How to check if is `object`?
```js
toString.call({});                      // "[object Object]"
Object.prototype.toString.call(obj);    // "[object Object]"
if (obj instanceof Object) {...}        // true
```    
##### 2. How to check `array`?
```js
const arr = [];

Array.isArray([]);                      // true, IE 9+
toString.call([]);                      // "[object Array]"
Object.prototype.toString.call(arr);    // "[object Array]"
if (arr instanceof Array) {...}         // true
```
##### 3. How to check `null`, `undefined`, `NaN`?
```js
val === null;             // true (if it is null)
val === undefined         // true (if it is undefined)
Number.isNaN(NaN)         // true
```

---
### References
 1. _Check if object is array?_ http://stackoverflow.com/questions/4775722/check-if-object-is-array
 2. 
