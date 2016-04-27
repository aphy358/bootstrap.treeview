# bootstrap.treeview 简介

从网上找了一个bootstrap样式的树形控件，然后我根据自己的需要做了些许改动，说不定你也会用得着。

## PreView

UI只是粗略設計，請各位見諒！

![View](https://github.com/aphy358/bootstrap.treeview-/blob/master/img/screenshot.jpg)


## Dependencies

- [jQuery v2.1.3 (>= 1.9.0)](http://jquery.com/)
- [Bootstrap v3.3.4](http://getbootstrap.com)
 

## Getting Started

### Usage

首先是引入样式文件和js文件.

```html
<!-- Required Stylesheets -->
<link href="./css/bootstrap-treeview.css" rel="stylesheet" />

<!-- Required Javascript -->
<script src="./js/jquery-1.11.3.min.js"></script>
<script src="./js/bootstrap.min.js"></script>
<script src="./js/bootstrap-treeview.js"></script>
```

基本用法参照原插件链接地址：https://github.com/jonmiles/bootstrap-treeview

### Difference with Original

1、首先，原插件需要再页面预留一个DOM元素：<div id="tree"></div>,改动之后，如果页面没有这个DOM元素，则将会自动添加。
	
2、其次，原插件在构建属控件时传入的参数格式非常复杂，不好操作，因此我扩展了一个方法Tree.prototype.initData，现在您只需传入如下格式的数据即可：

```html
// 可以通过指定nodeId和parentId来确立节点之间的父子关系。
var tree = [
    { text: "Parent", nodeId: 0, state: { expanded: true, } },
    { text: "Child", nodeId: 1, parentId: 0, state: { expanded: true, } },
    { text: "Grandchild", nodeId: 2, parentId: 1, state: { expanded: true, }, isLeaf: true, },
    { text: "Child", nodeId: 3, parentId: 0, state: { expanded: true, } },
    { text: "Grandchild", nodeId: 4, parentId: 3, state: { expanded: true, }, isLeaf: true, },
    { text: "Grandchild", nodeId: 5, parentId: 3, state: { expanded: true, }, isLeaf: true, },
];

$('#tree').treeview({
    data: tree
});

```

3、然后是节点的伸缩操作改动，原插件需要点击节点前的那个伸缩图标，但为了适应手机移动端的需要，改成了点击这一行即可响应伸缩事件。

4、样式文件从Bootstrap.css中提取了出来，这样就不需要引用大部头了。

