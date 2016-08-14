### Stack by Array
Use array as stack: 
```js
const stack = [];    // stack: []
stack.pop()          // undefined
stack.push(1)        // stack: [1]
stack.push(3)        // stack: [1, 3]
stack.pop()          // stack: [1], 3 is returned
stack[stack.length-1];    // peak()
```
### Queue by Array
```js
const queue = [];    // queue: []
queue.push(2);       // queue: [2]        
queue.push(4);       // queue: [2, 4]
const i = queue.shift()    // queue: [4], 2 is returned
```
### Sort Array
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