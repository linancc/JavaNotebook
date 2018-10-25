### HTML

1. html。xhtml，html5

   html是一个超文本标记语言，W3C组织制定的标准；从2.0开始，重要版本：html 4.01，xhtml 1.0，html 5；xhtml 不是html 的升级版本（标准很宽松）向xml 过度的标准；html 标准不严格：标签，属性不区分大小写，是否关闭，扩展名。。。；xhtml 要求严格，只是对html进行规范化处理，也扩展了一些标签；html5 是html 的升级版本，一统江山，把所有的设备，厂商的个性化标准；跨平台，跨浏览器，兼容不同的设备：H5技术；html5包含了html，xhtml中很多标签和标准，规范

2. html

   值的是超文本标记语言；不是一种编程语言，而是一种标记语言

   常用标签：

   标题 h1

   段落 p

   链接 a

备注：如何将HTML升级XHTML



清除浮动

```html
clear:left;
clear:right;
clear:both;
```

解决父级边框塌陷的方法

1. 浮动元素后面加空div

```html
html:
<div class="clear"></div>
css:
.clear{
	clear:both;
	margin:0;
	padding:0;
}
```

2. 设置父元素高度

3. 父级添加overflow属性

```html
overflow:hidden;
```

1. 父级添加伪类after（推荐）

```html
html:
<div id="father" class="clear">
    <div></div>
    <div></div>
    <div></div>
    <div></div>
</div>
css:
.clear:after{
    content: '';  在clear类后面添加内容为空
    display: block;  把添加的内容转化为块元素
    clear: both;  清除这个元素两边的浮动
}
```

```
总结：
1. 浮动元素后面加空div：很简单，空div会造成HTML代码冗余
2. 设置父元素的高度：很简单。元素固定高会降低元素可扩展
3. 父级添加overflow属性：很简单，但是有下拉列表框的场景不能用
4. 父级添加伪类after：写法稍微复杂，但是没有副作用，推荐使用
```

