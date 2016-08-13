# In the Real World
Make sure you have read **last chapter** _this - basics_ before you read following.

One reason JS looks complicated is because JS is dealing with something else such as: DOM, Async calls etc. Things get complecated, in real world's real interviews.

### 1. With DOM's Event Binding
```js
$('button').click(function(event) {
    console.log(this);
});
```
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
cal.calculate.sum1();             // ?
cal.calculate.sum2();             // ?
```

### Constructor

This is a hard one:
