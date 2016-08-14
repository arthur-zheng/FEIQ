# In the Real World
Make sure you have read last chapter _this - basics_ before you read following.

One reason Javascript looks complicated is: Javascript are usually used to deal with DOM, Async calls and libs written by random people... Things get complicated, in real world, in real interviews.

### 1. Callbacks Without Auto Binding

`setTimeout()` is a popular one in interviews: 
```js
const tom = {
    examAnswer: 'x = 100',
    startExam() {
        setTimeout(function() {
            console.log(`My answer is: ${this.examAnswer}`);
        }, 1000);
    }
}
tom.startExam();
```
Answer is code will not work as expected since `this` is `window` inside the callback.`forEach()` has the same issue:

```js
const daenerys = {
    home: "King's landing",
    dragons: [
        {name: 'Drogon', location: 'The Wall'},
        {name: 'Rhaegal', location: 'Castel Black'},
        {name: 'Viserion', location: 'Winterfell'}
    ],
    // trying to set dragon's location to daenerys.home
    dragonsGoHome() {
        // attention: callback in forEach()
        this.dragons.forEach(function(dragon) {
            dragon.location = this.home;        // this === window
        });
    }
}
daenerys.dragonAttack();
daenerys.dragons[0].home;    // undefined
```
The this will become `window` again in the callbacks. Why? because in the above `setTimeout()` or `forEach()`, callback is invoked in purely function form. Kind of like:

```js
// a function supports callback
function deleteDomNodesWithCallback(parentNode, callback) {
    // do the deleting stuff
    ...
    // callback is invoked as a purely function
    callback();
}
deleteDomNodesWithCallback(iAmTheNode, iAmCallback);
```
Since we know what just happened, how to **fix** `this` by specifying the right `this`?

```js
// Way 1:
// using 'that', or closure
const tom = {
    examAnswer: 'x = 100',
    startExam() {
        var that = this;
        setTimeout(function() {
            console.log(`My answer is: ${that.examAnswer}`);
        }, 1000);
    }
}
tom.startExam();

// Way 2:
// use bind(), a cleaner & better way
const tom = {
    examAnswer: 'x = 100',
    startExam() {
        setTimeout(function() {
            console.log(`My answer is: ${that.examAnswer}`);
        }.bind(this), 1000);
    }
}
tom.startExam();
```
And at last a fix for Daenerys:
```js
var daenerys = {
...
 dragonsGoHome() {
    var _that = this;         // created only for demo purpose
    this.dragons.forEach(function(dragon) {
        // inside the callback
        dragon.location = this.home;
    }.bind(this));           // `this` equals to _that
 }
...
// daenerys [dot] dragonsGoHome
daenerys.dragonsGoHome();
```
Since this part once confused me for a long time, please allow me to assume that you need a final explanation:

1. When we call `daenerys.dragonsGoHome()`, we pass `daenerys` into method `dragonsGoHome()` as `this`.
2. So inside `dragonsGoHome`, `this` equals to `daenerys` object.
3. The `bind(this)` is inside the same context/this-scope as `dragonsGoHome()`. So `this` equals `daenerys`.


### 2. Callbacks With Auto Binding

Some libary such as jQuery, or DOM API binds `this` for you in the background. Unlike above.

```js
// jQuery.js
$('button').click(function(event) {
    console.log(this);
});
// the button object will be logged

// Pure DOM API
document.querySelector('html').addEventListener('click', function() {
    console.log(this);
});
// the html DOM object will be logged

```
Keep in mind those functions' behavior.

### 3. HTML Inline (Auto Binding)
Not a recommended practise since we always want to seperate Representing (HTML) and Logic (Javascript).

```js
<button onclick="alert(this.tagName.toLowerCase());">
    Show this
</button>

// 'button'
```

### ???


### References:

1. _Understanding Javascript's this With Clarity, and Master It_: [http:\/\/javascriptissexy.com\/understand-javascripts-this-with-clarity-and-master-it\/](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)
2. _this_ (MDN) https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this