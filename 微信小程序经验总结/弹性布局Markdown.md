弹性布局的六个属性:
##  flex-direction：
 决定主轴的方向（即项目的排列方向）。
##   flex-wrap:
  默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。
##   flex-flow：
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。
## justify-content：
justify-content属性定义了项目在主轴上的对齐方式。
## align-items：
align-items属性定义项目在交叉轴上如何对齐。
## align-content:
align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

```
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
```
.box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```
```
.box {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```

```
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```

```
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```

```
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```






