# HTML and Browser Event

### 1. What is sementric html? Why do some people think it's useful?
https://www.wikiwand.com/en/Semantic_HTML

### 2. What is event bubbling and capturing?
Ref: http://www.quirksmode.org/js/events_order.html

### 3 What event doesn't bubble?

Any events specific to one element do not bubble: submit, focus, blur, load, unload, change, reset, scroll, most of the DOM events (DOMFocusIn, DOMFocusOut, DOMNodeRemoved, etc), mouseenter, mouseleave, etc

Ref: http://stackoverflow.com/questions/5574207/html-dom-which-events-do-not-bubble

### 4. How to cancel a `<a>` event using coding?
```js
event.preventDefault();
```
Ref: http://stackoverflow.com/questions/10276133/how-to-disable-html-links
