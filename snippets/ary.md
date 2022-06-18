---
title: Function arity
tags: function
expertise: advanced
cover: blog_images/trippy-chemicals.jpg
firstSeen: 2018-01-24T13:59:54+02:00
lastUpdated: 2020-10-18T20:24:28+03:00
---

-   功能：提取指定范围内的最大值

Creates a function that accepts up to `n` arguments, ignoring any additional arguments.

-   Call the provided function, `fn`, with up to `n` arguments, using `Array.prototype.slice()` and the spread operator (`...`).

```js
const ary =
	(fn, n) =>
	(...args) =>
		fn(...args.slice(0, n))
```

```js
const firstTwoMax = ary(Math.max, 2)
;[[2, 6, 'a'], [6, 4, 8], [10]].map((x) => firstTwoMax(...x)) // [6, 6, 10]
```

-slice() 方法可从已有的数组中返回选定的元素
-slice() 方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。 -注意： slice() 方法不会改变原始数组。
