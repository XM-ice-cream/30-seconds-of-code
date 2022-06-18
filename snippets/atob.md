---
title: Decode Base64 encoded string
tags: node,string
expertise: beginner
cover: blog_images/thread.jpg
firstSeen: 2018-01-17T21:43:21+02:00
lastUpdated: 2020-09-15T16:28:04+03:00
---

-   功能：根据给定的 base-64 编码的字符串创建一个 Buffer，并且使用 Buffer.toString('binary') 来返回解码后的字符串。
    binary：二进制

Decodes a string of data which has been encoded using base-64 encoding.

-   Create a `Buffer` for the given string with base-64 encoding.
-   Use `Buffer.prototype.toString()` to return the decoded string.

```js
const atob = (str) => Buffer.from(str, 'base64').toString('binary')
```

```js
atob('Zm9vYmFy') // 'foobar'
```
