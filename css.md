### 1. Difference between Block & Inline?

inline / block (use case):

 1. inline(only accepts left/right padding/margin, no top/bottom will take effect), block accepts all
 2. inline accepts vertical-align, blocks doesn’t
 3. block’s default width is 100%
 4. inline doesn’t accept width/height, block accepts all
 5. when a inline element is floated, it accepts width and height

Credit:
http://www.impressivewebs.com/difference-block-inline-css/

### 2. Different Ways to Hide an Element?

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

Credit: https://kitt.hodsden.org/blog/2013/07/5_3_ways_hide_element_css

### 3. Selectors
What are those selectors??
```css
s
```
Source: https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048

### 4. Centering
for centering, the ultimate way is to use flex. However, to support some old browsers, we need some classical approaches.

##### 1. Vertically align elements?
1. for inline elements
```css
vertical-align: center;
```
2. for block elements:
    1. use flex if you can
```css
.parent   { display: flex }
.children { align-self: center; }
/* or */
.parent   {
            display: flex;
            flex-direction: column;
            justify-content: center;
}
```
    1. use negative margin if know the height
```css
.parent { position: relative; }    /* to work with children's absolute position */
.children {
            position: absolute;
            height: 200px;
            margin-top: -100px;
            top: 50%;
}
```
    2. use transform is dont know the height
```css
.parent { position: relative; }
.children {
            position: relative;
            top: 50%;
            transform: translateY(-50%);
}
```

##### 2. Horizontally align Elements?
1. for inline elements:
```css
.item-parent {
        text-align: center;
}
```
2. for block-level elements
    1. use flex, supports multiple items as well:
```css
.parent {
            display: flex;
            justify-content: center;
}
```
    2. otherwise use margin: 0
```css
.children { margin: 0 auto; }
```

##### 3. Follow-up: How about both vertical and horizontal align?

1. Use flex:
```css
.parent {
    display: flex;
    justify-content: center;    /* this will center all items on the main axis */
}
.children {
    align-self: center;
}
```
2. Old fashion ways, the trick of 0
```css
/* https://www.smashingmagazine.com/2013/08/absolute-horizontal-vertical-centering-css/ */
.children {
        margin: auto;
        position: absolute;
        top: 0; left: 0; bottom: 0; right: 0;
}
```
3. use translate
```css
.parent { position: relative; }
.children {
        position: absolute;
}
```
Source: https://css-tricks.com/centering-css-complete-guide/

### 5. Text Space

#####How to display space in HTML text? 

`&nbsp;`
Note: there is a ; at the bottom
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
Source: Presonal experience

---
### Reference:
1. _How to write out HTML entity name (&amp;nbsp;, &amp;lt;, &amp;gt;, etc)?_ http://stackoverflow.com/questions/17427713/how-to-write-out-html-entity-name-nbsp-lt-gt-etc
2. _Does opacity:0 have exactly the same effect as visibility:hidden?_ http://stackoverflow.com/questions/272360/does-opacity0-have-exactly-the-same-effect-as-visibilityhidden?answertab=votes#tab-top
3. 