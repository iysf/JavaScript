## CSS继承
想要清楚继承底层运行原理，得去查看DOM文档的树图

某一段样式规则应用到元素上，这个规则再沿着树向下传播到后代。值也绝对不会向上传递，元素不会把值上传给祖先。

> 颜色可以继承

```css
body {
  color: red;
}
```
```html
<span>安抚请问废弃物</span>
```
那么其实它的DOM树结构 是 HTML > body > span span是属于body的子元素。所以会应用body标签定义的样式。

> 边框不可以继承

```css
div {
  border: solid 1px #000;
}
```
```html
<div>
  <span>安抚请问废弃物</span>
</div>
```
> 包括margin、padding、background都不能继承。

继承的值，没有优先级（并不是0优先级）。

> 考虑以下代码的运行原理

```css
* {
  color: red;
}
p#title {
  color: blue;
}
```
```html
<p id="title">p start 按时发解耦去排污费我去翻墙<em>em start 按时放进去我放弃 em end</em> p end </p>
```
最终通过运行可以发现，p标签的文字颜色为blue。但em的文字颜色却是红色的。明明是继承了p标签的颜色，为什么还是红色的？

因为通配选择器的优先级为0、继承的值是：没！有！优！先！级！（并不是0优先级）

通过以下小例子可以得知

```css
p {
  color: yellow !important;
}
```
```html
<p style="color: red;">撒覅解耦破千万级欧派发脾气欧文去<em>发请问</em></p>
```

### inherit

> inherit 使一个属性的值与父元素的值相同。指定继承

```css
div {
  color: blue;
  border: solid 1px #ccc;
}
p {
  color: inherit;
  border: inherit;
}
a {
  color: inherit;
  border: inherit;
}
```
```html
<div>
  <p>我去废弃物废弃物请问物权法<a href="#">全服务器我去</a></p>
</div>
```
