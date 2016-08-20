# DOM API
A lof of interviewer like to ask you how to manipulate DOM nodes. Sometimes using 3rd party lib such as jQuery is allowed, sometimes it is not.

This chapter focuses on native DOM APIs.

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

### Other DOM API
http://ourjs.com/detail/573a9cec88feaf2d031d24fc



---
### References:
1. _你应该知道的25道 Javascript 面试题_ http://web.jobbole.com/84723/
2. _You Don't Need jQuery_ http://ourjs.com/detail/573a9cec88feaf2d031d24fc