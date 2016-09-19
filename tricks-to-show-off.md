###1. Get Integer Part
Firstly, the classic ways:
```js
// Math.floor() works for positive only
Math.floor(-1.2);     // -1

// Math.ceil() works for negative only
Math.ceil(1.3);       //  2

// Math.round() works fine
Math.round(1.2);      //  1
Math.round(-1.2);     // -1

// ParseInt()
parseInt(1.2, 10);    // 1
parseInt(-1.2, 10);   //-1
```
Then, tricks probably won't help you pass the code review:
```js
~~1.1                 //  1
~~1.8                 //  1
~~(-1.1)              // -1
~~(-1.8)              // -1
~~-1.1                // -1
const three = ~~(10/3);

// another trick
console.log(1.2 | 0);   //  2
console.log(-1.2 | 0);  // -1

// another way using bit
1.2>>0                // 1
-1.2>>0               // -2
```
The reason bit works is that internally, bit operation is like:

1. convert the number from double-float to int
2. then do bit operations, |(or),  ~(revert) etc
3. then convert back to float

###2. Get Boolean
```js
// using !!
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
