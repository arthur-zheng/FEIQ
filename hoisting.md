#Hoisting

Hoisting means lifting.

It was actually created to _simplify_(wait, what?) Javascript originally, by avoiding referencing error. After hoisting, we can use a variable before it's declared (unlike Java).



###1. Simplest Form
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
The behavior that Javascript Engine (such as Google V8) lift the following declaration up is called `hoisting`

1. functions or variables declared as `var a = 1` or `var foo = function() {}`, will lift their left part. Such as`var a = undefined` and `var foo = undefined` will be lifted.
2. functions declared as `function foo() {...};` will be fully lifted to the top of the scope.

###2. With ES6
```js
function test() {
    console.log(val);
    let val = 1;
}
test();
```
We got an error says: `Uncaught ReferenceError: val is not defined`. This is because `let` and `const` will not be hoisted.

###3. ??