# frames.length===window.length

## `window.frames`,`window.length`

`window.frames`属性返回一个类似数组的对象，成员为页面内所有框架窗口，包括 frame 元素和 iframe 元素。`window.frames[0]`表示页面中第一个框架窗口。

如果 iframe 元素设置了 id 或 name 属性，那么就可以用属性值，引用这个 iframe 窗口。比如`<iframe name="myIFrame">`可以用`frames['myIFrame']`或者`frames.myIFrame`来引用。

frames 属性实际上是 window 对象的别名。

```js
frames === window; // true
```

> window.length 属性返回当前网页包含的框架总数。如果当前网页不包含 frame 和 iframe 元素，那么 window.length 就返回 0。

---

```js
window.frames.length === window.length; // true
```

> 上面代码表示，window.frames.length 与 window.length 应该是相等的。

参考：

[https://www.dazhuanlan.com/2020/04/01/5e84806a87386/](https://www.dazhuanlan.com/2020/04/01/5e84806a87386/) [https://www.w3cschool.cn/fetch_api/fetch_api-yqoj2nsu.html](https://www.w3cschool.cn/fetch_api/fetch_api-yqoj2nsu.html)
