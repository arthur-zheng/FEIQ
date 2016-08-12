# The _**this**_ keyword

The this keyword is always **confusing**. Especially when functions are invoked in different ways:

1. Purely function
2. Object method
3. Constructor
4. Indirectly using `apply()`, `call()` or `bind()`


Sometimes it looks even **more confusing** when combined with `=>` arrow functions. Do you know what does the following code snippets log?

### Question 1. Regular functions & Arrow functions

```js
function test() {
    this.calculate = {
      array: [1, 2, 3],
      sum: () => {
        console.log(this); // => ???
      },
      sum2() {
        console.log(this); // => ???  
      }
    };
};
var t = new test();
t.calculate.sum();
t.calculate.sum2();
```

