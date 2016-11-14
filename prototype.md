# Prototype

### What is prototype and what is constructor?
![](/assets/Screen Shot 2016-11-13 at 8.55.16 PM.png)

Ref: http://tobyho.com/2010/11/22/javascript-constructors-and/

### Some prototype and inheritance coding:
Write a `Person` class that we can specify `name`:
```js
function Person (name) {
    this.name = name;
}
```
Ok, now add a function to all the people instances so that they can tell you who they are by saying `hi, I am <name>`.
```js
Person.prototype.sayHi = function () {
    console.log(`hi, I am ${this.name}.`);
}
// Test it
const alice = new Person('Alice');
const tom = new Person('Tom');

alice.sayHi();        // 'hi, I am Alice.'
tom.sayHi();          // 'hi, I am Tom.'
```

Next, inheritance part.
Create another class called `Student` class.
that takes a `name` and `id` as argument, inherit from `Person` class (means using `Student` constructor).
```js
// constructor part
function Student (name, id) {
    Person.call(this, name);
    this.id = id;
}
// prototype part
Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

// Replace the "sayHello" method
Student.prototype.sayHi = function(){
    console.log("Hi, I'm " + this.firstName + ". My id is " + this.id + ".");
}; 
// Example usage:
var student1 = new Student("Tom", "10192");
student1.sayHi();
// "Hello, I'm Janet. My id is 10192."

// Check that instanceof works correctly
console.log(student1 instanceof Person); // true
console.log(student1 instanceof Student); // true

// More notes please check the ref link bellow
```
Ref/from: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript
