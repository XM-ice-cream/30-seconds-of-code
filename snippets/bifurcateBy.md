---
title: Bifurcate array based on function
tags: array
expertise: intermediate
cover: blog_images/canoe.jpg
firstSeen: 2018-02-14T12:13:07+02:00
lastUpdated: 2020-11-01T20:50:57+02:00
---

-功能：此段代码将数组按照指定的函数逻辑进行分组，满足函数条件的逻辑为真，放入第一个数组中，其它不满足的放入第二个数组 。这里运用了 Array.prototype.reduce() 和 Array.prototype.push() 相结合的形式，基于函数过滤逻辑，通过 Array.prototype.push() 函数将其添加到数组中

Splits values into two groups, based on the result of the given filtering function.

-   Use `Array.prototype.reduce()` and `Array.prototype.push()` to add elements to groups, based on the value returned by `fn` for each element.
-   If `fn` returns a truthy value for any element, add it to the first group, otherwise add it to the second group.

```js
const bifurcateBy = (arr, fn) =>
	arr.reduce(
		(acc, val, i) => (acc[fn(val, i) ? 0 : 1].push(val), acc),
		[[], []]
	)
```

```js
bifurcateBy(['beep', 'boop', 'foo', 'bar'], (x) => x[0] === 'b')
// [ ['beep', 'boop', 'bar'], ['foo'] ]
```
