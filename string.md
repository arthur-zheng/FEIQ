#String

### 1. Remove Space

1.1 How do you change " abc " to "abc"? (remove beginning and ending spaces)

```js
" abc  ".trim();    // "abc"
```

1.2 How do you change " a b c " to "abc"? (remove all spaces)

```js
" abc ".trim(); // "abc"
```

1.3 How do you change "a&nbsp;&nbsp;&nbsp;    b c" to "a b c" ? (Single space to multi-space)

```js
" abc ".trim(); // "abc"
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
