---
title: Add event listener to all targets
tags: browser,event
expertise: intermediate
author: chalarangelo
cover: blog_images/red-mountain.jpg
firstSeen: 2021-04-22T08:53:29+03:00
lastUpdated: 2021-04-22T08:53:29+03:00
---

-   当所有指定标签被点击时触发监听事件

Attaches an event listener to all the provided targets.

-   Use `Array.prototype.forEach()` and `EventTarget.addEventListener()` to attach the provided `listener` for the given event `type` to all `targets`.

```js
const addEventListenerAll = (targets, type, listener, options, useCapture) => {
	targets.forEach((target) =>
		target.addEventListener(type, listener, options, useCapture)
	)
}
```

```js
addEventListenerAll(document.querySelectorAll('a'), 'click', () =>
	console.log('Clicked a link')
)
// Logs 'Clicked a link' whenever any anchor element is clicked
```

-   参数注释
    /_
    targets:
    type:click,blur,load,change
    listener:监听到事件类型后执行的回调函数
    options(可选):①：capture:Boolean==>表示 listener 会在该类型的事件捕获阶段传播到该 EventTarget 时触发
    ②：once:Boolean==>表示 listener 在添加之后最多只调用一次。如果为 true,listener 会在其被调用之后自动移除
    ③：passive:Boolean==>设置为 true 时，表示 listener 永远不会调用 preventDefault().如果 listener 仍然调用这个函数，客户端将会忽略他抛出一个控制警告
    ④：AbortSignal,该 AbortSignal 的 abort()方法被调用时，监听器会被移除
    _/
