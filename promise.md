### Promise Basics


### Promise.all()

### Promise Wrapper
Write a function that returns a promise and takes `link as params`

```js
function get(url) {
    /* Your code here */
}

/* Usage */

// get zoo #123 's info
get('/zoo/123').then(data => displayZoo);

// takes multiple links and do something when all get returns
get(['/zoo/1', '/zoo/2', 'zoo/3']).then(data => compareZoos);

// internal code you dont need to worry about
function compareZoos() { /* ... */ }
```

### Traffic Lights
By using promise, write a function to simulate a dummy traffic light system:


1. Red light for 5s
2. Yellow light for 2s
3. Green light for 4s

```js
// red() yellow(), green() to use
function red() { console.log('red'); }
function yellow() { console.log('yellow'); }
function green() { console.log('green'); }

// your code here:
// Use Promise.resolve() etc
```
---
###References
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects
