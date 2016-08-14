#Hoisting

Hoisting means lifting.

It was actually created to _simplify_(wait, what?) Javascript originally, by avoiding referencing error. After hoisting, we can use a variable before it's declared (unlike Java).

###1. Definition and Example
```js
function test() {
    console.log(val);        // ?
    console.log(foo());     // ?
    var val = 1;
    function foo() {
        return 2;
    }
}
test();
```
Here's what actually happened:
```js
function test() {
    // a variable declaration will only be hoisted to it's own scope's top
    var val = undefined;
    function foo() {
        return 2;
    }
    console.log(val);        // val was lifted but is init as undefined
    console.log(foo());     // foo() was lifted
    val = 1;
}
test();
```


The behavior that Javascript Interpreter (such as Google V8) hoists/lifts the declaration part up to the scope's top is called `hoisting`.

### 2. Types of Hoisting

####1. Declare + Assign:
1. variables: `var val = 10`.
2. functions: `var foo = function() {...}`

For these forms, only the left/declaration part will be hoisted. As `var val = undefined`, `var foo = undefined` will be lifted to top.
```js
test() {
    ...
    var val = 100;
    var foo = function() {...};
}
// Becomes:
test() {
    var val = undefined;
    var foo = undefined;
    ...
    val = 100;
    foo = function() {...};
}
```
####2. Declare-only:
For functions declared as `function foo() {...};` will be fully lifted to the top of the scope.
```js
test() {
    var foo = 2;
    ...
    function foo() {...};
}
// Becomes:
test() {
    var foo;
    function foo() {...};
    // all declarations are on top
    foo = 2;
    ...
}
```

###2. With ES6
```js
function test() {
    console.log(val);
    let val = 1;
}
test();
```
We got an error says: `Uncaught ReferenceError: val is not defined`. This is because `let` and `const` will not be hoisted.

###3. A Little Bit More Complex (Ref.1):
```js
var num = 1;
function() {
    if (!num) {
        var num = 100;
    }
    console.log(num);
}
```
Answer is 100. Why? Here's what actually happens:
```js
var num = 1;
function() {
    var num = undefined;
    if (!num) {            // true
        var num = 100;
    }
    console.log(num);
}
```
Remember declaration will be hoisted to top of it's scope. And `if` doesn't create new scope for `var`.

What about we use const?
```js
const num = 1;
function() {
    if (!num) {
        const num = 100;
    }
    console.log(num);
}
```
Will get error: `Uncaught TypeError: Identifier 'num' has already been declared`. Because:
 
1. `const` will not be hoisted, thus we will get into `if`.
2. Then we are trying to declare `num` again with `const`, which is not allowed.

###References:
1. _JS: Explain “hoisting”_: http://lucybain.com/blog/2014/hoisting/
2. 