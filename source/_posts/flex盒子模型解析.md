---
title: flex盒子模型解析
date: 2017-02-20 17:22:44
categories:
  - web前端技术
tags: [css3,flex]
---

#### flex-flow 布局方向

    flex-direction 方向：水平或者垂直
    flex-wrap ：是否换行 wrap nowarp

    //示例：
    ul{
      flex-flow: row  wrap;
    }
    //相当于
    ul{
       flex-direction: row;
       flex-wrap: wrap;
    }

 <!--more-->

#### justify-content 主轴对齐方式

    justify-content: flex-start || flex-end || center || space-between || space-around

  - **space-between:** 两端对齐
  - **space-around:**  每个项目有相同的空间

#### align-items 垂直-即侧轴的对齐方式

    align-items: flex-start || flex-end || center || stretch || baseline

- **stretch** ：让每个`flex`项目的高度充满容器
- **baseline**： 基线对齐

#### align-content 多行的Flex容器
> 用来控制`Flex`项目在`Flex`容器里的排列方式，排列效果和`align-items`值一样，但除了`baseline`属性值
* **stretch** :会拉伸`flex`项目，让他们沿着侧轴适应容器可用的空间（多行自动分布侧轴的空间）
* **flex-start**：侧轴的顶部对齐，多行时自动换行，像默认的从上到下排列
* **flex-end**：让多行`Flex`项目靠着侧轴结束位置，flex项目从下到上排列
* **center**：多行在`flex`容器侧轴的中间位置展示

#### order 代表flex项目位置顺序
> 在不改变html结构的情况下调整位置 默认值是0

     li:first-child{order:1}//这个li会排在最后面跟z-index相似 当值越大越往后

#### flex-basis 宽度值 % || em || rem || px
> flex: 是 flex-grow、flex-shrink和flex-basis的速记

    flex: 0 1 auto;
    //相当于
    flex-grow: 0;
    flex-shrink: 1;
    flex-basis: auto;
### **flex-grow** 和**flex-shrink**
>属性控制`Flex`项目在容器有多余的空间如何放大（扩展），在没有额外空间又如何缩小。
> 他们可能接受`0`或者大于`0`的任何正数,`flex-grow`的默认值是`0`表示`Flex`项目不会增长,
> 取值为`0`就是一个开和关的按钮。`0`表示`flex-grow`开关是关闭的。
> flex-grow为1时代表开关打开了，容器使用屏幕宽度

* **flex-grow** 值默认是`0` 控制`flex`
* **flex-shrink** 值默认是`1`
* **flex-shrink** 值默认是`auto`

#### align-self  独立控制flex项目在侧轴的位置
> 单独的flex项目不影响其它的flex项目

     align-self ：auto || flex-start || flex-end || center || baseline || stretch

    li:first-of-type{
       align-self ：flex-start
      }

> 我是搬运工，文章参考: https://www.w3cplus.com/css3/understanding-flexbox-everything-you-need-to-know.html