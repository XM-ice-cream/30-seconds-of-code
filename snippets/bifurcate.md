---
title: Bifurcate array based on values（根据值分岔阵列）
tags: array
expertise: intermediate
cover: blog_images/two-cities.jpg
firstSeen: 2018-02-14T12:13:07+02:00
lastUpdated: 2020-11-01T20:50:57+02:00
---

-   功能：此函数包含两个参数，类型都为数组，依据第二个参数的真假条件，将一个参数的数组进行分组，条件为真的放入第一个数组，其它的放入第二个数组。  
    bifucate:分支

Splits values into two groups, based on the result of the given `filter` array.

-   Use `Array.prototype.reduce()` and `Array.prototype.push()` to add elements to groups, based on `filter`.
-   If `filter` has a truthy value for any element, add it to the first group, otherwise add it to the second group.

```js
const bifurcate = (arr, filter) =>
	arr.reduce(
		(acc, val, i) => (acc[filter[i] ? 0 : 1].push(val), acc),
		[[], []]
	)
```

```js
bifurcate(['beep', 'boop', 'foo', 'bar'], [true, true, false, true])
// [ ['beep', 'boop', 'bar'], ['foo'] ]
```
