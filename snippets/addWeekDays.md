---
title: Add weekdays to date
tags: date
expertise: intermediate
cover: blog_images/digital-nomad-9.jpg
firstSeen: 2020-10-11T16:51:39+03:00
lastUpdated: 2021-01-08T00:23:44+02:00
---

-   功能：在添加给定的工作天数后计算日期（如果是周末，通过添加一天或者两天再次更新他，使他成为一个工作日）

Calculates the date after adding the given number of business days.

-   Use `Array.from()` to construct an array with `length` equal to the `count` of business days to be added.
-   Use `Array.prototype.reduce()` to iterate over the array, starting from `startDate` and incrementing, using `Date.prototype.getDate()` and `Date.prototype.setDate()`.
-   If the current `date` is on a weekend, update it again by adding either one day or two days to make it a weekday.
-   **NOTE:** Does not take official holidays into account.（不考虑法定节假日）

```js
const addWeekDays = (startDate, count) =>
	Array.from({ length: count }).reduce((date) => {
		date = new Date(date.setDate(date.getDate() + 1))
		if (date.getDay() % 6 === 0)
			date = new Date(
				date.setDate(date.getDate() + (date.getDay() / 6 + 1))
			)
		return date
	}, startDate)
```

```js
addWeekDays(new Date('Oct 09, 2020'), 5) // 'Oct 16, 2020'
addWeekDays(new Date('Oct 12, 2020'), 5) // 'Oct 19, 2020'
```

/\*
解释：
`Array.from()` ：从类似数组或可迭代对象创建一个新的(浅拷贝)的数组实例
Array.from 可以通过以下方式来创建数组对象 1. 伪数组(拥有一个 length 属性和若干索引属性的任意对象) 2. 可迭代对象(可以获取对象中的元素，如 Map 和 Set 等)
Array.from()方法有一个可选参数 mapFn,让你可以在最后生成的数组上，再执行一次 map 方法后再返回。
即 Array.from(obj,mapFn,thisArg)相当于 Array.from(obj).map(mapFn,thisArg);
`reduce()`:常用语求和和求乘积
arr.reduce(function(prev, cur, index, arr) {
console.log(prev, cur, index);
return prev + cur;
}，0) //注意这里设置了初始值

\*/
