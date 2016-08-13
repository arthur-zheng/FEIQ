# The **_this_** keyword

The this keyword is always **confusing**. Especially when functions are invoked in different ways:

1. As a method, like `obj.foo()`, this is exactly the same as most languages, such as java.
2. As purely function, like `foo()`
3. As a constructor, like `new Student()`
4. Indirectly using `apply()`, `call()` or `bind()`

Sometimes it looks even **more confusing** when combined with `=>` arrow functions. Do you know what does the following code snippets log?

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
jon.fullName();                // "Jon Snow"
jon.weapon.use();              // "Pew, Longclaw used."
```
Invoked as method works the same as java. And it's fundamental of all our future theories.

`fullName` method was invoked as a method of `jon`. Because there is a 'jon.' right before it. So `jon` will passed into `fullName()` as its `this`.

**Takeaway**: _Anything_ before the **dot** will passed into the method as the method's `this` keyword.

### 2. As Function

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
A little bit more tricky in here combining tip-1 and tip-2:

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
Since there's nothing or dot before the `fullNameOutside`, it is invoked as a pure function, `window` will be the `this`. 

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

Takeaway: Steps when a constructor is called \(in the above code for example\):

1. Create a new empty object {} and use Tom to point to it.
2. pass the newly created object `Tom` as _this_ into to the constructor \(`Student()`\).
3. Go through the constructor.

So, in here, the `this` will be the new object, `Tom`.

### 4. As with `apply()`, `call()` and `bind()`
Since this is so flexible, what if sometime we want to mannally control the this? `apply()`, `call()` and `bind()` was created to do this.
```js
function showFullName() {
    return `${this.firstName} ${this.lastName}`;
}
showFullName();                // error, firstName and lastName are undefined
const jon = {
    firstName: 'Jon',
    lastName:  'Snow'
}
showFullName.apply(jon);       // 'Jon Snow'
showFullName.call(jon);        // 'Jon Snow'
showFullName.bind(jon)();      // 'Jon Snow'
```
### 5. Arrow functions

In ECMAScript 6, arraw functions was introduced. One of arrow function's features is that it **automatically** bind _this_ for you.
```js
const jon = {
    firstName: 'Jon',
    lastName: 'Snow',
    fullName: () => `${this.firstName} ${this.lastName}`,
    getThis: () => this
}
jon.fullName();                // "undefined undefined"
jon.getThis();                 // window

// inside test() scope
function test() {
    const jon = {
        firstName: 'Jon',
        lastName: 'Snow',
        fullName: () => `${this.firstName} ${this.lastName}`,
        getThis: () => this
    }
    jon.fullName();             // "undefined undefined"
    jon.getThis();              // window
}
test();
```
This is what Babel (https://babeljs.io/repl) compiles from above:

```js
function test() {
    var _this = this;
    var jon = {
        firstName: 'Jon',
        lastName: 'Snow',
        fullName: function fullName() {
            return _this.firstName + ' ' + _this.lastName;
        },
        getThis: function getThis() {
            return _this;
        }
    };
    jon.fullName();             // "undefined undefined"
    jon.getThis();              // window
}
test();
```
We can tell is that, the arrow function binds _the scope which wraps the outside object_ with _this_.

### References:
1. _Understanding Javascript's this With Clarity, and Master It_: [http:\/\/javascriptissexy.com\/understand-javascripts-this-with-clarity-and-master-it\/](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)
2. 
