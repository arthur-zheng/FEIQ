# The **_this_** keyword

------

The this keyword is always **confusing**. Especially when functions are invoked in different ways:

1. As a method, like `obj.foo()`
2. As purely function, like `foo()`
3. As a constructor, like `new Student()`
4. Indirectly using `apply()`,`call()`,`bind()`and `()=>{}`

### 1. As a Method, as in Java
```js
const jon = {    
    firstName: 'Jon',    
    lastName: 'Snow',
    fullName() {        
        console.log(`${this.firstName} ${this.lastName}`)                    
    }
    weapon: {
        name: 'Longclaw',
        use() {
            console.log('Pew, ${this.name} used.');
         }
     }
}
// jon [dot] fullName()
jon.fullName();                // "Jon Snow"
// jon.weapon [dot] use()
jon.weapon.use();              // "Pew, Longclaw used."
```

Invoked as method works the same as Java.

`fullName` method was invoked as a method of `jon`. Because there is a `jon.` right before it. So `jon` will passed into `fullName()` as its `this`. Samely, `jon.weapon` was passed into `use()` as `this`.

**Takeaway**: _Anything_ before the last **[dot]** will be passed into the method as the method's `this` keyword.

But there's nothing or even [dot] before the function? Read on.

### 2. As Purely Function (Global)

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
console.log(this === window); // true
console.log(this.document === document); // true
```

So, the `foo`\( or `window.foo`\) was invoked and thus the **default**`this`\( or`window`\) was logged.

**Takeaway**: In browser, `window` is the default `this`.

A little bit more tricky interview question in here, by combining tip-1 and tip-2:

```js
const jon = {
    firstName: 'Jon',
    lastName: 'Snow',
    fullName() { 
        console.log(`${this.firstName} ${this.lastName}`)
    }
}
// pull the funtion out
const fullNameOutside = jon.fullName;
// invoke it as pure function
fullNameOutsite();            // "undefined undefined", as this is window
```
Since there's nothing or [dot] before the `fullNameOutside`, it is invoked as a **pure function**, thus `window` will be the `this`.

**Takeaway**: Where/how a functions was **declared** is much less important than **how** the function was **invoked**.

### 3. As Constructor
```js
// a constructor
function Student(id) {
    this.id = id;
    console.log(this.id);      // ?
}
// new instance
const Tom = new Student(10092);
```

**Takeaway**: What happends when a constructor is invoked \(in the above code for example\):

1. A new empty object `{}` was created.
2. Tom was pointed to the new empty object.
3. `Tom` was passed into to the constructor `Student()` as `this`.
3. Execute the constructor.

So, in here, the `this` will be the new instance object `Tom`.

### 4. As with `apply()`, `call()` and `bind()`
Since this is so flexible, what if sometime we want to mannally control the `this`? `apply()`, `call()` and `bind()` was created to do solve this problem.
```js
function showFullName() {
    return `${this.firstName} ${this.lastName}`;
}
showFullName();                // "undefined undefined"

const jon = {
    firstName: 'Jon',
    lastName:  'Snow'
}
showFullName.apply(jon);       // 'Jon Snow'
showFullName.call(jon);        // 'Jon Snow'
showFullName.bind(jon)();      // 'Jon Snow'
```

### 5. [dot]-Rule Exception: Arrow Functions
Sorry the above [dot] rule doesn't work in here.

In ECMAScript 6, arrow functions was introduced. One of arrow function's features is that it **automatically** bind `this` for you when arrow function was declared. This feature will definitly confuse a lot of beginners.

```js
const jon = {
    firstName: 'Jon',
    lastName: 'Snow',

    fullName: () => `${this.firstName} ${this.lastName}`,
    // Same as:
    fullName: function() {
        return `${this.firstName} ${this.lastName}`
    }.bind(this);

    getThis: () => this,
    // Same as
    getThis: function() {return this}.bind(this)
}
jon.fullName();                // "undefined undefined"
jon.getThis();                 // window
```
What Babel (https://babeljs.io/repl) compiles proves our conclusion:

Before:
```js
function test() {
    const jon = {
        firstName: 'Jon',
        lastName: 'Snow',
        fullName: () => `${this.firstName} ${this.lastName}`,
    }
    jon.fullName();             // "undefined undefined"
}
test();
```
After:
```js
function test() {
    var _this = this;
    var jon = {
        firstName: 'Jon',
        lastName: 'Snow',
        fullName: function fullName() {
            return _this.firstName + ' ' + _this.lastName;
        }
    };
    jon.fullName();             // "undefined undefined"
}
test();
```
We can tell is that, the arrow function binds _the scope which wraps the outside object_ with _this_.

**Takeaway**: The [dot] rule **doesn't** work with arrow function since `this` was already **invisibly** binded/specified as soon as arrow function was declared.

### Conclusions
1. The default `this` is window in browser.
2. Whatever was before the [dot] will be passed into the method as `this`. This rule **doesn't work** with arrow functions, since their `this` was already binded when being declared.
3. How one function was **invoked** is way more important than how/where it was **declared**.

---
### References:
1. _Understanding Javascript's this With Clarity, and Master It_: [http:\/\/javascriptissexy.com\/understand-javascripts-this-with-clarity-and-master-it\/](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)
2. stackoverflow: http://stackoverflow.com/questions/2130241/pass-correct-this-context-to-settimeout-callback
3. _this_ (MDN) https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this
