### Difference between Block & Inline?
inline / block (use case)

http://www.impressivewebs.com/difference-block-inline-css/

inline(only accepts left/right padding/margin, no top/bottom), block accepts all.
inline accepts vertical-align, blocks doesn’t
block’s default width is 100%
if inline is float, will become block
inline doesn’t accept width/height (but accepts vertical-align

### How to hide an Element?
WAYS TO HIDE AN ELEMENT

https://kitt.hodsden.org/blog/2013/07/5_3_ways_hide_element_css

display: none
visibility: hidden (like opacity: 0)
opacity: 0
position:absolute; z-index: 1000; margin:-100px; ???
left:-9999px; position:relative ???
left:-9999px; position:absolute ???
transform: translateX(-9999px)

### Vertical align elements?

### Horizontal align Elements?

### Both Vertical and Horizontal Align?


### Text Space

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
