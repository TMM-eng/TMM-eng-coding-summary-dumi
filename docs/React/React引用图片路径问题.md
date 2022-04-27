# React 引用图片路径问题

用 create-react-app 脚手架搭建 react 项目:`npx create-react-app demoname`

1. 如果图片放在了 src 下的 assets 的 img 文件夹中，这种情况下直接用 src 会出现问题，但是用 require 是可以的 ![1](../images/react/1.png)

```html
<img src={[require("../assets/img/2x.png")]} alt=""/>
```

**注意：require 中只能放字符串，不能放变量**

后来看了看 create-react-app 的官网，官网明确说出最好将图片样式等放在 public 文件夹中，是可以用的`<img src="../images/photo.png"/>`这种形式的如下图官网 [https://facebook.github.io/create-react-app/docs/using-the-public-folder#when-to-use-the-public-folde](https://facebook.github.io/create-react-app/docs/using-the-public-folder#when-to-use-the-public-folder)

![2](../images/react/2.png)

改装后的文件夹如下，将图片放在了 public 文件夹中： ![3](../images/react/3.png) 这样就可以用了

```html
<img src="assets/logo-ant.svg" alt="logo" className="logo" />
```

2. 图片存放于 assets 文件夹下时

```js
// 引入方式方式1
import logo from '@/assets/images/logo.png';

// 引入方式方式2
const logo = require('@/assets/images/logo.png');
```

render 中使用

```
<img src={logo} alt="图片" />
<div style={{ background: `url(${logo}) no-repeat center` }}>背景图</div>
```

```
// 不用引入，直接行内引入路径
<img src={require("@/assets/images/logo.png")} alt="logo"/>
```

**注意：require 中只能放字符串，不能放变量**
