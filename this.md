# The **_this_** keyword

The this keyword is always **confusing**. Especially when functions are invoked in different ways:

1. Purely as function, like `foo()`
2. Object's method, like `obj.foo()`
3. Constructor, like `new Student()`
4. Indirectly using `apply()`, `call()` or `bind()`

Sometimes it looks even **more confusing** when combined with `=>` arrow functions. Do you know what does the following code snippets log?

### 1. As Function

```js
function foo() {
    console.log(this);    // this means, whatever passed into foo as this
}
foo();                    // ?
```

Keep in mind that everything in Browser happens within the `window` scope:

```js
var a = 100;              // a dangerous global variable
console.log(window.a)     // 100
console.log(this.a)       // 100
```

So, the `foo`\( or `window.foo`\) was invoked and the **default**`this`\( or`window`\) was logged.

**Takeaway**: In browser, `window` is the default `this`.

### 2. As Method

```js
const jon = {
    firstName: 'Jon',
    lastName: 'Snow',
    fullName() {
        console.log(`${this.firstName} ${this.lastName}`)
    }
}
jon.fullName();            // ?
```

fullName method was invoked as a method of `jon`. Because there is a 'jon.' right before it. So `jon` will passed into `fullName()` as its `this`.

**Takeaway**: _Anything_ before the **dot** will passed into the method as the method's `this` keyword.

### 3. As Constructor

```js
function Student(id) {
    this.id = id;
    console.log(this.id);    // ?
}
const Tom = new Student(10092);
```

Takeaway: Steps when a constructor is called \(in the above code for example\):

1. Create a new empty object {} and use Tom to point to it.
2. pass the newly created object `Tom` as _this_ into to the constructor \(`Student()`\).
3. Go through the constructor.

So, in here, the this will be the new object, `Tom`.

### 4. As with `apply()`, `call()` and `bind()`

### 5. Arrow functions

In ECMAScript 6, arraw functions was introduced. One of arrow function's features is that it **automatically** bind _this_ for you.

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

### Ref:

1. _Understanding Javascript's this With Clarity, and Master It_: [http:\/\/javascriptissexy.com\/understand-javascripts-this-with-clarity-and-master-it\/](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

