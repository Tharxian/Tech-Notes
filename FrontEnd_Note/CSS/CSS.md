# CSS
css 是规定 Web 样式的语言，如果把 HTML 比喻成给房子的毛坯，那么 css 则是给房子装修

**css的注释语法：**`/* COMMENT */`
## CSS的导入方式
css通常由选择器、属性和属性值构成，基础样式为
```
选择器
{
    属性1: 属性值1;
    属性2: 属性值2;
}
```
记得使用英文分号隔开每组属性和属性值。选择器可以包扩任意数量的属性，属性与值以键值的形式呈现，与Python中的字典类似。

```html
<style>
    p
    {   color: blue;
        font-size: 16px;  
    }
</style>
```
### css 的三种导入方式：
1. 内联样式 Inline Styles
   >   直接在所需要的地方写css。
   ```html
    <h2 style="color:green;"> Your content </h2>
   ```

2. 内部样式表 Internal Stylesheet
    > 将css放置在html的head中。
   ```html
   <head>
       <!--内部样式表 Internal Stylesheet-->
       <style>
       h1
       {   color: blue;
           font-size: 16px;  
       }
       </style>
   </head>
   ```

3. 外部样式表 External Stylesheet
    >  将css的内容单独保存为.css的文件，以便在多个html中都可直接使用。
    ```html
    <head>
        <link rel="stylesheet" href="./css/h1style.css">
    </head>
    ```

三种导入方式的优先级：内联样式 > 内部样式表 > 外部样式表

## CSS选择器
选择器选定的是你希望进行自定义的内容，选择器有以下几种：

**比较简单的**
- 元素选择器
    > 选择某特定的HTML标签，不加上其他的筛选条件。如选择所有的段落`<p>`标签：
    ```css
    p
    {   color: blue;
        font-size: 16px;  
    }
    ```
    
- 类选择器
   > 选择具备某特殊class的标签，不加上其他的筛选条件。如选择带有`highlight`类标签：
    ```css
    .highlight
    {   color: yellowgreen;
        font-family: "KaiTi";
    }
    ```

- ID选择器
  > 选择具备某特殊id的标签，不加上其他的筛选条件。如选择带有`header`id标签：
    ```css
    #header
    {   color: pink;
        font-size: 16px;  
    }
    ```

- 通用选择器
   > 没有筛选，选择所有元素进行风格定义：
   ```css
    *
    {   color: black;
        font-size: 16px;  
    }
   ```
类选择器和id选择器为最为常用的两个选择器。当不同的选择器出现冲突时，他们的优先级为：id > class > 标签

**较为复杂的**
- 子元素选择器
  >HTML的父子关系指的就是嵌套，例如
    ```html
    <div class="father">
        <p class="son">
        </p>
    </div>
    ```
    >这里 p 即是 div 的子元素， 而子元素选择器是用来自定义某父元素下所有具备某特殊类的子元素，然而对于其他具备该类的标签则不被影响，如：
    ```css
    .father > .son
    {   color: black;
        font-size: 16px;  
    }
    ```


- 后代选择器（包含选择器）
  > 选择某父标签下所有的标签
  ```css
  .father p
  {   color: black;
      font-size: 16px;  
  }
  ```
- 并集选择器（兄弟选择器）
   > 指定某个标签，使紧跟其后的另一个指定标签被选中；如我们需要将所有h3标签后所跟的p标签的背景调为黄色，则
   ```css
    h3  + p
    {   background-color : yellow;
    }
   ```

- 伪类选择器
   > 将某特定的事件（e.g.鼠标悬停）视为类，因为和一般的类不同，所有称为**伪类**。然后以此作为筛选条件，进行选择：
   ```html
   <p id="element">Click Here</p>
   ```
   ```css
    #element:hover
    {   background-color : blue;

    }
   ```

## CSS的常用属性
复合属性案例 `<font>`
## 字体
```html
<h1 style="font: 50px 'serif';">这是一个h1标题</h1>
```
<h1 style="font: 50px 'serif';">这是一个h1标题</h1>

### 行间距
```html
<p style="line-height:40px">
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>
```
<p style="line-height:40px">
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>


### 块元素的长宽
以下为一个块元素
```html
<div class="block">
    BLOCK
</div>
```
直接输出，不做调整的结果是
<div class="block">
    BLOCK
</div>

将以下内容加入到 head 中，可以实现对block类的元素进行自定义，其中包括了width和height
```html
<style>
    .block{
        background-color:pink;
        color : white;
        font-size: 50px;
        width: 160px;
        height: 160px;
    }
</style>
```
```html
<div style="background-color:pink;
        color : white;
        font-size: 50px;
        width: 160px;
        height: 160px;">
    BLOCK
</div>
```
或者可以写为内联样式，效果为
<div style="background-color:pink;
        color : white;
        font-size: 50px;
        width: 160px;
        height: 160px;">
    BLOCK
</div>

### 行内块元素的长宽
行内块元素的大致结构为：`text block text`, e.g.
```html
<p><b>Google Chrome:</b>
    <img src="./chrome.png" alt="">
</p>
```

<p><b>Google Chrome:</b>
    <img src="./chrome.png" alt="">
</p>
这是不做任何调整得到的结果，当我们设置它的长宽后，有

```html
<p><b>Google Chrome:</b> 
    <img src="./chrome.png" alt="无法显示"
    style="height:20px;
           width:20px;">
    in height of 20px.
</p>

<p><b>Google Chrome:</b> 
    <img src="./chrome.png" alt="无法显示"
    style="height:50px;
           width:50px;">
    in height of 20px.
</p>
```
<p><b>Google Chrome:</b> 
    <img src="./chrome.png" alt="无法显示"
    style="height:20px;
           width:20px;">
    in height of 20px.
</p>

<p><b>Google Chrome:</b> 
    <img src="./chrome.png" alt="无法显示"
    style="height:50px;
           width:50px;">
    in height of 20px.
</p>

### 行内元素的长宽
行内元素本身是不支持长宽的选择的，它的长宽收到字体大小的影响；然而，如果我们把行内元素转换为行内块元素，他就支持像行内块一样调整长宽。

实现转换要用到的关键词为`display`, 以下为某HTML文件的body
```html
<body>
    <div>这是一个普通的块元素</div>
    <span>这是一个普通的行内元素</span>
</body>
```
显示效果为：
<div>这是一个普通的块元素</div>
<span>这是一个普通的行内元素</span>

此时对`<span>`进行长宽的自定义是无效的，但是加上了display属性后
```html
<span style="width:3px; height:50; display:block;">
    这是一个普通的行内元素
</span>
```
<span style="width:90px; height:50; display:block;">
    这是一个普通的行内元素
</span>
<br>

>转换后对长宽的改变不会改变字体，而是用一个无形的框框住了字，而长宽的调整实则是对这个框生效。   

如果要将块元素转换为行内元素，使用 `display:inline;`

## CSS盒模型
网页设计中的每个元素都可视为一个矩形的盒子，而这个盒子由四种属性定义：
1. 边界 Margin
2. 边框 Border
3. 填充 Padding
4. 内容 Content

这4项在一起合称为 MBPC 模型。

### 边界 Margin

基本语法 
```css
margin: 10px 10px 20px 30px; /*四个数字分别代表的是上右下左(顺时针)*/
margin：10px 20px 30px;      /*上，左右，下*/
margin：20px 30px;           /*上下，左右*/
margin：20px；               /*四条边*/
margin-left: 200%;          /*除了px，也可以加百分比*/
```
针对特定的HTML标签，也可以写
```css
p{margin:10px 10px 20px 30px;}
```

### 边框 Border
**border-style**

基本语法：`border=style: 属性值`，属性值有以下这些：
<table border = 1>
    <tr>
       <th>属性值</th>
       <th>说明</th>
    </tr>
    <tr>
        <th>none</th>
        <th>无边框</th>
    </tr>
    <tr>
        <th>hidden</th>
        <th>无边框，和none一样；用于解决表的边框冲突</th>
    </tr>
    <tr>
        <th>dottted</th>
        <th>点状虚线</th>
    </tr>
    <tr>
        <th>dashed</th>
        <th>线状虚线</th>
    </tr><tr>
        <th>solid</th>
        <th>实线</th>
    </tr><tr>
        <th>double</th>
        <th>双线，其宽度取决于border-width的值</th>
    </tr><tr>
        <th>groove</th>
        <th>3D凹槽边框，其效果取决于border-width的值</th>
    </tr><tr>
        <th>ridge</th>
        <th>山脊壮边框，其效果取决于border-width的值</th>
    </tr><tr>
        <th>inset</th>
        <th>使界面沉入感边框，其效果取决于border-width的值</th>
    </tr>
    <tr>
        <th>outset</th>
        <th>使界面浮出感边框，其效果取决于border-width的值</th>
    </tr>
</table>
 
 border-style 允许有多个键值，例如：
```css
border-style:solid dotted dashed;
```
 border-style允许分开设置四条边的值，如
```css
border-style-top: solid;
border-style-right: dashed;
border-style-bottom: dotted;
border-style-left: none;
```

 **border-width**
```css
border-width: thin;
border-width: 10px;
border-width: 10px thin medium thick; /*对应上右下左*/
```
<table border = 1>
    <tr>
       <th>属性值</th>
       <th>说明</th>
    </tr>
    <tr>
        <th>medium</th>
        <th>默认值</th>
    </tr>
    <tr>
        <th>thin</th>
        <th>小于默认值</th>
    </tr>
    <tr>
        <th>thick</th>
        <th>大于默认值</th>
    </tr>
</table>
和border-style一样，border-width也可以在后面加上 top、right、bottom 和 left

**border-color** 的语法和上述两个类似，省略。

border的复合属性结构为 `border: width style color;`

### 填充 Padding
```css
padding: 长度;
padding: 百分比;

padding-top: 长度或百分比;
padding-right: 长度或百分比;
padding-bottom: 长度或百分比;
padding-left: 长度或百分比;

p
{padding-top: 长度或百分比;
padding-right: 长度或百分比;
padding-bottom: 长度或百分比;
padding-left: 长度或百分比;
}
```

## CSS浮动布局

网页布局的几种方式：
- 标准流（普通流、文档流），按照元素的书写顺序一次排序
- 浮动
- 定位
- `Flexbox`和`Grid`（自适应布局）   
各种布局的本质都是摆盒子，通常一个网页汇报课多种不同的布局。

浮动是一种可以灵活的布局，允许多个块元素并排摆放。基本语法
```css
选择器{
    float: left/right/none;
}
```
浮动的三大特性：
- 脱标：脱离标准流
- 一行显示，顶部对齐
- 具备行内块元素特性

在head中配置以下style
```html
<style>
        .father{
            background-color: bisque;
            border: 3px dashed black;
        }

        .left-son{
            width: 50%;
            height: 100px;
            background-color: yellowgreen;
            float: left;
            color: white;
            font-size: 50px;
            overflow:hidden;
        }

        .right-son{
            width: 50%;
            height: 100px;
            background-color: burlywood;
            float: right;
            color: black;
            font-size: 50px;
            overflow:hidden;
        }
    </style>
```
加入`overflow:hidden;`以避免之后输入的文字卡进先前的浮动中。

在body中输入以下,效果为；
```html
    <div class="father">
        <div class="left-son">这是左边</div>
        <div class="right-son">这是右边</div>
    </div> 
```
<div style="background-color: bisque;
            border: 3px dashed black;">
        <div style="width: 50%;
            height: 100px;
            background-color: yellowgreen;
            float: left;
            color: white;
            font-size: 50px;
            overflow:hidden;">这是左边</div>
        <div style="width: 50%;
            height: 100px;
            background-color: burlywood;
            float: right;
            color: black;
            font-size: 50px;
            overflow:hidden;">这是右边</div>
</div>


## 定位

定位相对于浮动更好控制，但是不如浮动灵活。定位的种类有：
- 相对定位：相对于元素在文档流中的正常位置进行定位
- 绝对定位：相对于已经定位的祖先元素进行定位，不占据文档流。
- 固定定位：相对于浏览器窗口进行定位，不占据文档流，固定在屏幕上的位置，不随滚动而移动。
```css
选择器{
    position:relative | absolute | fixed;
}
```