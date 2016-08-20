#Array (Queue, Stack, Tree)

### 1. `forEach()` and `map()`
What's the difference between `forEach()` and `map()`?

 1. Return value
 2. ?
 3. ?

What does
```js
const arr = [0, 0, 0, 0, 1, 0, 0, 0];
arr.forEach(function(val, index) {
    if (val === 1) break;
    else arr[index] = 3;
})
console.log(arr);        // ?
```
Answer is `Uncaught SyntaxError: Illegal break statement`. There's no built-in ability to `break` in `forEach`.

### 2. `every()` and `some()`
What's the difference between `every()` and `some()`?


### 3. Implement Stack using Array
How to use array as stack?
```js
const stack = [];    // stack: []
stack.pop()          // undefined
stack.push(1)        // stack: [1]
stack.push(3)        // stack: [1, 3]
stack.pop()          // stack: [1], 3 is returned
stack[stack.length-1];    // peak()
```
### 4. Implement Queue using Array
How to use array as queue?
```js
const queue = [];    // queue: []
queue.push(2);       // queue: [2]        
queue.push(4);       // queue: [2, 4]
const i = queue.shift()    // queue: [4], 2 is returned
```
### 5. Sort Array
What will the following return?
```js
[1,2,11,3].sort();
```
Answer is: `[1, 11, 2, 3]`.

A little surprise right? Reason is `sort(comparator)`'s default comparator treats array items as `string`.

Fix:
```js
[1, 2, 11, 3].sort((a, b) => a - b);
// [1, 2, 3, 11]
```
More about `Array.prototype.sort()`: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort

### References:
1. _9 JavaScript Tips You May Not Know_
http://codetunnel.io/9-javascript-tips-you-may-not-know/
2. _Interviewing a front-end developer_ http://blog.sourcing.io/interview-questions?utm_source=ourjs.com
3. _How to short circuit Array.forEach like calling break_ http://stackoverflow.com/questions/2641347/how-to-short-circuit-array-foreach-like-calling-break