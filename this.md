# The **this** keyword

The this keyword is always confusing. Especial when a function is invoked in different ways or combining with arrow functions.

Do you know what does the following code snippets log?

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

