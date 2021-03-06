#String

### 1. Remove Spaces

1.1 How do you change " abc " to "abc"? (remove beginning and ending spaces)

```js
" abc  ".trim();    // "abc"
```

1.2 How do you change " a b c " to "abc"? (remove all spaces)

```js
" a b c ".replace(' ', '');
```

1.3 How do you change "a&nbsp;&nbsp;&nbsp;    b c" to "a b c" ? (Single space to multi-space)

```js
// failed: replace doesnt work recursively
" a    b c".replace(' ', '').split('').join(' ');

// Using Regex
" a    b c".replace( /\s+/g, ' ' );
// Ref: http://stackoverflow.com/questions/1981349/regex-to-replace-multiple-spaces-with-a-single-space
```

### 2. Implement `repeatify()`

Implement `repeatify()`:

```js
String.prototype.repeatify = String.prototype.repeatify ||
function(times) {
    /* write your own here */
}
// how it works
'Aoo'.repeatify(3); // 'AooAooAoo'
```
One of the answers could be:
```js
String.prototype.repeatify = String.prototype.repeatify || function(times) {
    // avoid concat for better performance:
    // like: str = ''; str += this;
    const str = [];
    for (var i = 0; i < times; i++) {
        str.push(this);
    }
    return str.join('');
};
```
Another faster approach using binary search
```js
//
String.prototype.repeat = function (times) {
    if(times === 1) return this;
    var halfString = String.prototype.repeat.call(this, Math.floor(times/2));
    return half + half + (times & 1 ? this : '');
}
```
A tricky way:
```js
// Ref: http://stackoverflow.com/questions/202605/repeat-string-javascript
String.prototype.repeat = function(num) {
    return new Array(num + 1).join(this);
}
```
### 3. Add space to String

Write a function to add a space to string.
```js
String.prototype.addSpace = function() {
 /* your code here */
}
"abc".addSpace(); // "a b c"
```
One of the solution is using `Array.prototype.split()` and `String.prototype.join()`:
```js
String.prototype.addSpace = function() {
 return this.split('').join(' ');
}
```

### 4. Check Palindrome
How to check if a string is palindrome?
```js
function isPalindrome(str) {
    return (str == str.trim().toLowerCase().split('').reverse().join(''));
}
```

### 5. All .toString()
Difference between all the `toString()`, like:
```js
const arr = [1,2,3],
      obj = {},
      num = 1,
      nul = null,
      undef;

// for arrays
// Array.prototype.toString is more useful
Array.prototype.toString.call(arr);    // '1,2,3'
Object.prototype.toString.call(arr);   // '[object Array]'
Number.prototype.toString.call(arr);   // error

// Array.prototype.toString works with objects
Array.prototype.toString.call(obj);    // '[object Object]'
Object.prototype.toString.call(obj);   // '[object Object]'
Number.prototype.toString.call(obj);   // error

// Number.prototype.toString seems only work for numbers
Array.prototype.toString.call(num);    // '[object Number]'
Object.prototype.toString.call(num);   // '[object Number]'
Number.prototype.toString.call(num);   // '12'

// Array.prototype.toString seems only work with array/object
Array.prototype.toString.call(nul);    // error
Object.prototype.toString.call(nul);   // '[object Null]'
Number.prototype.toString.call(nul);   // error

// Object.prototype.toString works with anything
Array.prototype.toString.call(undef);  // error
Object.prototype.toString.call(undef); // '[object Undefined]'
Number.prototype.toString.call(undef); // error
```


