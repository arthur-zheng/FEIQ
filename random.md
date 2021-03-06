#Random
Random questions related to web dev.

### 1. What is same-origin policy?
##### For security purpose, two website which are NOT from the same origin cannot share:

1. Cookies, localStorage, IndexDB
2. DOM
2. Ajax

Same-origin must have the same:

1. domain name (google.com vs apple.com)
2. protocol (http vs https)
3. port number (4080 vs 80)

PS: A page may change its own origin with some limitations. A script can set the value of document.domain to its current domain or a superdomain of its current domain. If it sets it to a superdomain of its current domain, the shorter domain is used for subsequent origin checks.

For example, assume a script in the document at http://store.company.com/dir/other.html executes the following statement: Like:
```js
document.domain = "company.com";
```
More info:
Ref: https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy

### 2. How to get around of same-origin policy?

##### We can use multiple approaches to get around same-origin policy, such as:
1. JSONP (Only support `GET`, more info: http://stackoverflow.com/questions/3839966/can-anyone-explain-what-jsonp-is-in-layman-terms, and (Chinese): http://www.cnblogs.com/dowinning/archive/2012/04/19/json-jsonp-jquery.html)
2. Server delegation (server does the request to different origin)
3. WebSocket (WebSocket have no same-origin policy)
4. CORS (Cross-Origin Resource Sharing)

### What will happen when you type in a URL and hit `enter`?
http://stackoverflow.com/questions/2092527/what-happens-when-you-type-in-a-url-in-browser

### Get vs Post?
http://stackoverflow.com/questions/3477333/what-is-the-difference-between-post-and-get

### Put vs Post in Restful API?
http://stackoverflow.com/questions/630453/put-vs-post-in-rest

