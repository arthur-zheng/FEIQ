# The **_this_** keyword

The this keyword is always **confusing**. Especially when functions are invoked in different ways:

1. Purely function, like `foo()`
2. Object method, like `obj.foo()`
3. Constructor, like `new Student()`
4. Indirectly using `apply()`, `call()` or `bind()`

Sometimes it looks even **more confusing** when combined with `=>` arrow functions. Do you know what does the following code snippets log?

### 1. Regular functions & Arrow functions

```js
// a constructor
function Calculator() {
    // object inside the constructor
    this.calculate = {
      array: [1, 2, 3],
      sum1: () => {
        console.log(this);
      },
      sum2() {
        console.log(this);
      }
    };
};
var cal = new Calculator();
cal.calculate.sum1();        // ?
cal.calculate.sum2();        // ?
```

