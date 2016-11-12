// array flatten
```js
var a = [1,2,[3],[4,[5,6]],7,8];
// way 1
function flattern(a) {
    return a.reduce((result,i)=>{
        return result.concat(Array.isArray(i)? flattern(i) : i);
    }, []);
}
// way 2
function flattern(a) {
    var stack = [], result = [];
    stack = stack.concat(a);
    while (stack.length) {
        let i = stack.pop();
        if (Array.isArray(i)) stack = stack.concat(i);
        else result.unshift(i);
    }
    return result;
}
flattern(a);
```

