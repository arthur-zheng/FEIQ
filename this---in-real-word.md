# In the Real World
Make sure you have read **last chapter** _this - basics_ before you read following.

One reason JS looks complicated is because JS is dealing with something else such as: DOM, Async calls etc. Things get complecated, in real world's real interviews.

### 1. With DOM's Event Binding
```js
// jQuery.js
$('button').click(function(event) {
    console.log(this);
});
// the button object will be logged

// Pure DOM API
document.querySelector('html').addEventListener('click', function() {
    alert(this);
});
// the html DOM object will be logged
```
This is because jQuery/DOM API binds `this` for you in the background. Unlike `setTimeout()` which doesn't do the same.

### 1. With DOM's Event Binding

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
