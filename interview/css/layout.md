## 布局相关
---

## position的值， relative和absolute分别是相对于谁进行定位的？  :id=position
1. absolute：生成绝对定位的元素，相对于 static 定位以外的第一个祖先元素进行定位
1. fixed：生成绝对定位的元素，相对于浏览器窗口进行定位。 （IE6不支持）
1. relative：生成相对定位的元素，相对于其在普通流中的位置进行定位
1. static：默认值。没有定位，元素出现在正常的流中

## 解释下浮动和它的工作原理？  :id=float
1. 浮动元素脱离文档流，不占据空间（引起“高度塌陷”现象）
1. 浮动元素碰到包含它的边框或者浮动元素的边框停留。

## 浮动元素引起的问题  :id=float-pro
1. 父元素的高度无法被撑开，影响与父元素同级的元素
1. 与浮动元素同级的非浮动元素会跟随其后
1. 若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构

## 什么是外边距重叠？重叠的结果是什么？  :id=margin-overlap
外边距重叠就是margin-collapse。

在CSS当中，相邻的两个盒子（可能是兄弟关系也可能是祖先关系）的外边距可以结合成一个单独的外边距。这种合并外边距的方式被称为折叠，并且因而所结合成的外边距称为折叠外边距。

折叠结果遵循下列计算规则：

1. 两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。
1. 两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。
1. 两个外边距一正一负时，折叠结果是两者的相加的和。