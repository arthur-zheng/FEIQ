###1. Use ~~ to Get Integer Part
```js
// Math.floor() works for positive only
Math.floor(-1.2);     // -1

// Math.ceil() works for negative only
Math.ceil(1.3);       //  2

// Math.round() works fine
Math.round(1.2);      //  1
Math.round(-1.2);     // -1

// a trick probably won't pass your code review
// or JS
~~1.1                 //  1
~~1.8                 //  1
~~(-1.1)              // -1
~~(-1.8)              // -1
~~-1.1                // -1
const three = ~~(10/3);
```
Because ~ operater will parse the number to integer before revert bits.
```
// The following is not a perfect way,
// for doesn't work with negative numbers


```

###2. Use !! to parse Boolean
```js
!!5        // true
!!true     // true
!!''       // false
!!null     // false
!![]       // true
```

###3. Odd, Even
```js
function isOdd(n) {
    return !!(n & 1);
}
isOdd(12);            // false
isOdd(1);             // true

// Pay attention that following returns 0
12 & 1 === 0          // 0, instead of true
(12 & 1) === 0        // true
```
---
### References:
1. 装逼指南
2. useless es5:
https://rainsoft.io/make-your-javascript-code-shide-knockout-old-es5-hack/
