# DOM
A lof of interviewer like to ask you how to manipulate DOM nodes. Sometimes using 3rd party lib such as jQuery is allowed, sometimes it is not.

This chapter focuses on native DOM APIs.

### 1. Basic manipulation to make sure you are familar with DOM API
1.1 Create add some text into the `<h1 id='target'></h1>`
```js
//
```
1.2 Create a span with text content `hello` and append it to the `<div id='target'></div>`
```js
//
```
1.3 As shown bellow, a `<ul>` has multiple `<li>`, add event to all of the `<li>` so that when it's clicked, alerts the index of it.
```js
//
```
1.4 Count number of a given node's children
```js
//
```

### Create a function that, given a DOM Element on the page, will visit the element itself and all of its descendents (not just its immediate children). For each element visited, the function should pass that element to a provided callback function.
The arguments to the function should be:
```js
a DOM element
a callback function (that takes a DOM element as its argument)
```
DFS:
```js
function Traverse(p_element,p_callback) {
    p_callback(p_element);
    var list = p_element.children;
    for (var i = 0; i < list.length; i++) {
        Traverse(list[i],p_callback); // recursive call
    }
}
```

### Give all elements inside html DOM a different color
```js
// Need verify
[].forEach.call($('*'), function(ele) {
    ele.style.outline = "1px solid #" + (~~(Math.random() * (1 << 24))).toString(16);
});
```

### Other DOM API
http://ourjs.com/detail/573a9cec88feaf2d031d24fc

### Node Object vs Element Object?
http://stackoverflow.com/questions/9979172/difference-between-node-object-and-element-object

### `textContent` vs `createTextNode()`?
They are the same except: for security perspective,`createTextNode()`will escape string and show them as they are.
http://stackoverflow.com/questions/31643204/textnode-or-textcontent

---
### References:
1. _你应该知道的25道 Javascript 面试题_ http://web.jobbole.com/84723/
2. _You Don't Need jQuery_ http://ourjs.com/detail/573a9cec88feaf2d031d24fc