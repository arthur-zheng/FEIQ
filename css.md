### 1. Difference between Block & Inline?

inline / block (use case)
http://www.impressivewebs.com/difference-block-inline-css/

 1. inline(only accepts left/right padding/margin, no top/bottom), block accepts all.
 2. inline accepts vertical-align, blocks doesn’t
 3. block’s default width is 100%
 4. if inline is float, will become block
 5. inline doesn’t accept width/height (but accepts vertical-align

### 2. Different Ways to Hide an Element?

https://kitt.hodsden.org/blog/2013/07/5_3_ways_hide_element_css

```css
// More common
display: none;
visibility: hidden;
opacity: 0;

// Tricky
position: absolute;
z-index: 1000;
margin: -100px; ???
left:-9999px;
position:relative ???
left:-9999px;
position:absolute; ???
transform: translateX(-9999px);
```

#####Follow-up: What's the difference between `visibility: none` and `opacity: 0`?

Click event. Element with `visibility: none`**doesn't** respond to click-event. But `opacity: 0` element does.

### 3. Vertical align elements?

### 4. Horizontal align Elements?

##### Follow-up: How about both vertical and horizontal align?




### ?. Text Space

#####How to display space in HTML text?

Answer: &amp;nbsp;

#####How to display the text `&nbsp;`?

```js
// Text we want to display exactly:
...
The text 'nbsp;' means 'space'
...
```
Answer:
```js
The text 'a&amp;nbsp;' means 'space'    // use &amp; to escape ;
```

### Reference:
1. _How to write out HTML entity name (&amp;nbsp;, &amp;lt;, &amp;gt;, etc)_ http://stackoverflow.com/questions/17427713/how-to-write-out-html-entity-name-nbsp-lt-gt-etc
