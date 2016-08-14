# Closure

### What is closure?

```js
// Closure example
function outer() {
    const val = 1;       // val is inside inner()'s closure
    return function inner() {
        console.log(val);
    }
}
```

Closure is created when the following happens:

1. A function `inner()` is created.
2. Inside `inner()`, some variable references to something **out of** `inner()`. Like `val`;
3. The referenced outer variable `val` becomes a closure variable and will always exist until no more referenced.

The above process called closure.

###1. Most Classical Question
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
The answer is `10`.

Because the function `a[5]` references a variable `i` which is outside. And the `i` will be always there. Since all the `i` referenced by a[0], a[1], a[2]... are the same **outer** **one**, all of them will be the same value: 10 (what the i became at the end).
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
Yes, `11` and `12` will be logged. This proves same `i` was **shared** and **modified**.

### 2. Follow up: How to fix

Then follow up will be: how do you fix it?
```js
// Way 1: Use function:
const arr = [];
for (var i=0; i < 10; i++) {
    arr[i] = (function(val) {    // line-4
        return function() {
            console.log(val);
        }            
    })(i);                       // pass i as innner function's val
}
arr[5]();         // 5
arr[8]();         // 8
```
As i is a primitive variable. We pass it by value. Means we are creating a copy and pass it into `line-4`'s function in every loop. No i is `shared` now.

```js
// Way 2: Use let
const arr = [];
for (let i=0; i < 10; i++) {
    arr[i] = function() {
        console.log(i);
    }
}
arr[5]();        // 5
arr[8]();        // 8
```
This is one of the situation `let` was created for.
For each loop, a new `i` was created. And none of them is shared.

### 3. What will be logged?
```js
// Question 1
(function(x) {
    return (function(y) {
        console.log(x);        // what will be logged?
    })(2);
})(1);

// Question 2
(function(y){
    return (function(y){
        console.log(y);        // what will be logged?
    })(2);
})(1);
```
### 4. When do you need it? [none coding]
Create private variables:
```js
//
```

### 5. What are the good and bad part of closure? [none coding]
```js
//
```


###References:
1. 你应该知道的25道 Javascript 面试题