---
title: Binary function arity（二元函数参数数量）
tags: function
expertise: intermediate
author: chalarangelo
cover: blog_images/blue-bird.jpg
firstSeen: 2020-05-13T13:36:36+03:00
lastUpdated: 2020-10-18T23:04:45+03:00
---

-   功能：创建一个最多接受两个参数的函数，忽略任何其他函数

Creates a function that accepts up to two arguments, ignoring any additional arguments.

-   Call the provided function, `fn`, with the first two arguments given.

```js
const binary = (fn) => (a, b) => fn(a, b)
```

```js
;['2', '1', '0'].map(binary(Math.max)) // [2, 1, 2]
```
