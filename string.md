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
// TODO
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
### 3. Add space to String

Write a function to add a space to string.
```js
String.prototype.addSpace = function() {
 /* your code here */
}
"abc".addSpace; // "a b c"
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
