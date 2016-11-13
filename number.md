#Number
### 1. Round() and toFixed()
1.1 How to round a number to integer?
```js
// http://www.w3schools.com/jsref/jsref_round.asp
// The round() method rounds a number to the nearest integer.
// Note: 2.49 will be rounded down, 2.5 will be rounded up.

Math.round(10.4);      // 10
Math.round(12.5);      // 13
```
1.2 How to round a decimal

```js
// http://www.w3schools.com/jsref/jsref_tofixed.asp
// The toFixed() method converts a number into a string, keeping a specified number of decimals.

// Note:

// Since javascript is using float to represent a int,
// sometimes the result is not predictible, like:

(1.5).toFixed()         // 2
(1.05).toFixed(1)       // 1.1        rounded up
(1.005).toFixed(2)      // 1.00       rounded down
(1.04).toFixed(1);      // 1.0        works as expected
```
### 2. Number.prototype.toString()
```js
(100).toString();       // '100'
(8).toString(2);        // '1000'
(16).toString(16);      // '10'
```
More info please check chapter - String.

