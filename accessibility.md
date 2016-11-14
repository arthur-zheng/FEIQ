### Enable a element to be tab-able?
Use tabIndex.
That are:

1. some elements are born to be tab-able. Such as `<a>`, `<input>` etc.
2. The sequence of tab-able elements when pressed tab is how they appear in `.html` file.
2. to enable an element to be tab-able, add `tabIndex='0'` to it.
3. to change tab-able elements' sequence. change tabIndex to `1,2,3...`
4. to disable tab-able, use `tabIndex = '-1'`

ref: https://www.paciellogroup.com/blog/2014/08/using-the-tabindex-attribute/

### Removing The Dotted Outline

https://css-tricks.com/removing-the-dotted-outline/
