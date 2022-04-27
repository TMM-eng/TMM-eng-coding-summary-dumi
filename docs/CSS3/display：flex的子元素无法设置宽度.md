## display：flex 的子元素无法设置宽度

使用 display:flex 制作轮播图的时候，想让每张轮播图的宽度 width="100%",即屏幕的宽度，但是设置了没有用，是因为 dispaly:flex 是流式布局，子元素有 flex-shrink 属性，表示在父元素宽度不够的情况下是自动收缩，0 表示不自动收缩，1 表示自动收缩；所以将子元素（图片）添加属性：flex-shrink:0;即可

### flex-shrink 属性

flex-shrink 属性定义了项目的缩小比例，默认为 1，即如果空间不足，该项目将缩小。

```css
.item {
  flex-shrink: <number>; /* default 1 */
}
```

如果所有项目的 flex-shrink 属性都为 1，当空间不足时，都将等比例缩小。如果一个项目的 flex-shrink 属性为 0，其他项目都为 1，则空间不足时，前者不缩小。

负值对该属性无效。

参考：[http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
