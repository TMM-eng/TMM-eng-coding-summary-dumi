# 在 react 中渲染 html 代码

有时候需要动态渲染后台传过来的 html 代码文本，但是 react 的 JSX 防注入攻击使得大括号里的 html 代码全部变成字符串进行渲染，而不是 html 代码例子：

```html
<div dangerouslySetInnerHTML="{{__html:" code}}></div>
```

更多方式：

```js
function createMarkup() {
  return { __html: 'First &nbsp;&nbsp;&nbsp; Second' };
}

function MyComponent() {
  return <div dangerouslySetInnerHTML={createMarkup()}></div>;
}
```

格式：

```js
<div dangerouslySetInnerHTML={{ __html: 返回的html代码片段 }}></div>
```

原理：

1. dangerouslySetInnerHTMl 是 React 标签的一个属性，类似于 angular 的 ng-bind；

2. 有 2 个{{}}，第一{}代表 jsx 语法开始，第二个是代表 dangerouslySetInnerHTML 接收的是一个对象键值对;

3. 既可以插入 DOM，又可以插入字符串；
