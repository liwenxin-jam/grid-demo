>flexbox是一维布局，他只能在一条直线上放置你的内容区块；而grid是一个二维布局。前面也简单说到，你可以根据你的设计需求，将内容区块放置到任何你想要放的地方。IE10+默认支持CSS Grid Layout模块功能之外，其他的浏览器Chrome、Safari、Opera和Firefox都需要重新设置（启用开发中的实验性网络平台功能）。

- 在Chrome浏览器中开启CSS-Grid-Layout模块功能比较简单，只需要在您的浏览器地址栏中输入：chrome://flags，回车后在列表清单中找到“启用实验性网络平台功能”（#enable-experimental-web-platform-features），一个更为简单的方法，可以直接在浏览器地址栏中输入网址：chrome://flags#enable-experimental-web-platform-features立马定位需要的选项，然后点击“启用”(enable)按钮。

可以给父容器的display属性设置为grid或者inline-grid来定义一个网格。这样你就可以使用grid-template-columns和grid-template-rows属性来创建一个网格。在这个示例中，创建了一个三列网格，其中三个列的列宽是100px，并且指定列与列之间的间距为10px。同时网格具有三行，每行的高度是自动的，另外行与行之间的间距是10px。简单点说就是一个三行三列的网格，并且列与列之间，行与行之间的间距都是10px。

- 默认以下栗子的Dom结构都是如此

```html
<div class="wrapper">
    <div class="box a">A</div>
    <div class="box b">B</div>
    <div class="box c">C</div>
    <div class="box d">D</div>
    <div class="box e">E</div>
    <div class="box f">F</div>
    <div class="box g">G</div>
    <div class="box h">H</div>
    <div class="box i">I</div>
    <div class="box j">J</div>
</div>
```

- 三列网格布局，核心样式代码是.wrapper。

```html
<style type="text/css">
body {
    padding: 50px;
}
.wrapper {
    display: grid;
    grid-template-columns: 100px 10px 100px 10px 100px;  /*指定了列宽100px、列间距10px*/
    grid-template-rows: auto 10px auto;  /*指定了行宽auto、行间距10px*/
}
.box {
    background-color: #444;
    color: #fff;
    font-size: 150%;
    padding: 20px;
}
.b, .d, .g, .i { 
    background-color: red; 
}
</style>
```

- 单元格占位区域，注意grid-column-start、grid-column-end、grid-row-start、grid-row-end的使用，默认都是从1开始算起。网格线的简写方式，其实就是grid-column和grid-row的start与end值合并在一起，两者之间用/来分隔。

```html
<style type="text/css">
body {
    padding: 50px;
}
.wrapper {
    display: grid;
    grid-template-columns: 100px 10px 100px 10px 100px 10px 100px;
    grid-template-rows: auto 10px auto 10px auto;
}
.box {
    background-color: #444;
    color: #fff;
    font-size: 150%;
    padding: 20px;
    text-align: center;
}
.a {
    grid-column-start: 1;
    grid-column-end: 2;
    grid-row-start: 1;
    grid-row-end: 2;
}
.b {
    grid-column-start: 3;
    grid-column-end: 4;
    grid-row-start: 1;
    grid-row-end: 2;
}
.c {
    grid-column-start: 5;
    grid-column-end: 6;
    grid-row-start: 1;
    grid-row-end: 2;
}
.d {
    grid-column-start: 7;
    grid-column-end: 8;
    grid-row-start: 1;
    grid-row-end: 2;
}
.e {
    grid-column-start: 1;
    grid-column-end: 2;
    grid-row-start: 3;
    grid-row-end: 4;
}
.f {
    grid-column-start: 3;
    grid-column-end: 4;
    grid-row-start: 3;
    grid-row-end: 4;
}
.g {
    grid-column-start: 5;
    grid-column-end: 6;
    grid-row-start: 3;
    grid-row-end: 4;
}
.h {
    grid-column-start: 7;
    grid-column-end: 8;
    grid-row-start: 3;
    grid-row-end: 4;
}
.i {
    grid-column-start: 1;
    grid-column-end: 2;
    grid-row-start: 5;
    grid-row-end: 6;
}
.j {
    grid-column-start: 3;
    grid-column-end: 4;
    grid-row-start: 5;
    grid-row-end: 6;
}
/*简写方式*/
.a{ grid-column: 1 / 2; grid-row: 1 / 2; } 
.b { grid-column: 3 / 4; grid-row: 1 / 2; } 
.c { grid-column: 5 / 6; grid-row: 1 / 2; } 
.d { grid-column: 7 / 8; grid-row: 1 / 2; } 
.e { grid-column: 1 / 2; grid-row: 3 / 4; } 
.f { grid-column: 3 / 4; grid-row: 3 / 4; } 
.g { grid-column: 5 / 6; grid-row: 3 / 4; } 
.h { grid-column: 7 / 8; grid-row: 3 / 4; } 
.i { grid-column: 1 / 2; grid-row: 5 / 6; } 
.j { grid-column: 3 / 4; grid-row: 5 / 6; }
/*覆盖样式，将a和f的位置对调*/
.a {
    grid-column-start: 3;
    grid-column-end: 4;
    grid-row-start: 3;
    grid-row-end: 4;
    background: red;
}
.f {
    grid-column-start: 1;
    grid-column-end: 2;
    grid-row-start: 1;
    grid-row-end: 2;
    background: orange;
}
</style>
```


以上栗子都是参照“大漠”老师关于Grid系列的几篇文章，但在我本机测试只看到部分效果生效，原因不明。如果有兴趣想了解深入一些的，建议可以点击以下参考文献的链接，自己尝试一下测试。

- 参考文献
1、[CSS Grid布局：什么是网格布局](https://www.w3cplus.com/css3/what-is-css-grid-layout.html)
2、[CSS Grid布局：浏览器开启CSS Grid Layout](https://www.w3cplus.com/css3/how-to-enable-support-for-grid-layout-in-various-browsers.html)
3、[CSS Grid布局：网格单元格布局](https://www.w3cplus.com/css3/line-base-placement-layout.html)
4、[CSS Grid布局：合并单元格布局](https://www.w3cplus.com/css3/css-grid-layout-merge-cells.html)




