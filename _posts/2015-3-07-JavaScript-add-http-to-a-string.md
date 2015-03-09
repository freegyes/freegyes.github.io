---
layout: post
title: JavaScript: add http:// to a string if it doesn't have it
tags:
- javascript
---

Prepend http:// if the string starts with no protocol.

```javascript
function addHttp(url) {
   if (!/^(f|ht)tps?:\/\//i.test(url)) {
      url = "http://" + url;
   }
   return url;
}
```

