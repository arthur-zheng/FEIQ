###1. Use ~~ to Get Integer Part
```js
~~1.1     // 1
~~1.8     // 1
~~(-1.1)  // -1
~~(-1.8)  // -1
~~-1.1    // -1

// Works like Java
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
