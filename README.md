# this

What does the following log?

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

