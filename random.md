#Random
Random questions related to web dev.

### 1. What is same-origin policy and how to get around of it?
##### 1.1 same-origin policy:
For security purpose, two website which are NOT from the same origin cannot share:

1. Cookies, localStorage, IndexDB
2. DOM
2. Ajax

Same-origin must have the same:

1. domain name (google.com vs apple.com)
2. protocol (http vs https)
3. port number (4080 vs 80)

##### 1.2 We can use multiple approaches to get around same-origin policy, such as:
1. JSONP (Only support `GET`, more info: http://stackoverflow.com/questions/3839966/can-anyone-explain-what-jsonp-is-in-layman-terms)
2. Server delegation (server does the request to different origin)
3. WebSocket (WebSocket have no same-origin policy)
4. CORS (Cross-Origin Resource Sharing)

### What will happen when you type in a URL and hit `enter`?
http://stackoverflow.com/questions/2092527/what-happens-when-you-type-in-a-url-in-browser


