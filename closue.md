# Closure

### Definition
Closure is created when the following happens:

1. A function `foo()` is created.
2. Inside `foo()`, some variable references to something **out of** `foo()`.
3. The referenced outer variable becomes a closure variable and will always exist until no more referenced.

### Example:
A common interview question starts like this:
```js
// what will be logged?
const array = [];
for (var i=0; i < 10; i++) {
    array[i] = function() {
        console.log(i);
    }
}
a[5]();          // ?
```
The answer is 10.
The function `a[5]` references a variable `i` which is outside. And the `i` will be always there. Since all the `i` referenced by a[0], a[1], a[2]... are the same **outer** **one**, all of them will be the same value: 10 (what the i became at the end).
```js
const arr = [];
for (var i=0; i < 10; i++) {
    arr[i] = function() {
        i++;
        console.log(i);
    }
}
arr[5]();        // ?
arr[6]();        // ?
```
Yes, 11 and 12 will be logged. This means same `i` was shared and modified.

### How to fix

Then follow up will be: how do you fix it?

Way 1: Use function:
```js
// 
```
Way 2: Use let
```js
// use let

```

### When do you need it?
```
var that = this;
if (this.options.destroyOnHide) {
    setTimeout(function() {
        that.tip.destroy()
    }, 1000);
}
```
Create private variables:
```js
//
```
### Advanced Questions
