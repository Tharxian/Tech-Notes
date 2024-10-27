# HTML

## 1. HTML标签
<a href = "https://www.w3cschool.cn/html5">Cheatsheet</a>

HTML 分单标签和双标签

- 单标签例子：`<input = "text">`

- 双标签例子：`<p> some content </p>`

## 2. HTML的结构

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
HTML文档的主要内容都在body里面。

## 3. 常见的文本标签

- 标题标签 `<h1>...</h1>`，数字是几表示是几级别标。

- 段落标签 `<p>...</p>`

- 字体标签
    - 字体加粗 `<b>...</b>`
    - 下划线 `<u>...</u>`
    - 删除线 `<s>...</s>`
  
- 无序列表标签 （类似 $\LaTeX$ 中的 \begin{itemize}）
```html
<ul>
    <li>
        Your content here
    </li>
</ul>
```

- 有序列表，把无序列表中的`<ul>`改成`<ol>`

- HTML注释`<!-- Comment -->`

- 表格标签
```html
<table border = 1> 
    <!-- 数字代表表格边框的宽度 -->
    <tr>
        <!-- tr为table row，每有一个tr就多一行 -->
        <th>
            Column 1 
        </th>
        <th>
            <!-- th为table head -->
            Column 2
        </th>
        <th>
            Column 3
        </th>
    </tr>
            <!-- td为table data -->
        <td>
            content 1
        </td>
        <td>
            content 2
        </td>
        <td>
            content 3
        </td>
    </tr>
</table>
```
效果为：
<table border = 1> 
    <tr>
        <th>
            Column 1
        </th>
        <th>
            Column 2
        </th>
        <th>
            Column 3
        </th>
    </tr>
        <td>
            content 1
        </td>
        <td>
            content 2
        </td>
        <td>
            content 3
        </td>
    </tr>
</table>

- 换行标签 `<br>`,分割线标签`<hr>`

## HTML标签中的属性
表格标签就是一个带有属性的标签。

标签属性的标准语法`<标签名 属性名 = 属性内容>`，一个标签可以包含多个属性，常见的带有属性的标签有：

- 超链接 `<a href="https://www.google.com" targe = "_blank">Google</a>`
  - _self 在当前标签页打开
  - _blank 在新的标签页打开
  - _parent 在上一级的标签页打开，若不存在上一级，则和_self一样
  - _top 在最前面的标签页打开，若不存在上一级，则和_self一样

- 图片 `<img src = "example.png" alt = "">`
  - alt 指当图片无法正常加载是显示的代替文字如 `<img src = "example.png" alt = "找不到这个图片">` 会显示

<img src = "example.png" width = "200" alt = "找不到这个图片">

有些属性只属于某唯一的标签，而有些属性可以适用于多种标签。例如：class, id, style等。

## 块元素和行内元素
### 块元素
块元素通常从新的一行开始，并占据整行的宽度；常见的块元素有：div, p, h1, ul, ol, li, table, form 等

### 行内元素
行内元素不会独占一行，他们只占据内容所需要的宽度，行内元素不可以包块块元素，但是可以包扩其他行内元素。
常见的行内元素有 span, a, strong, em, img, br, input 等

### `<Div>`
div可以创建一个网页中的**块**，如下为某网页导航栏；
```html
<div class="nav">
        <b>Navigator </b>
        <a href="#">🔗Link 1</a>
        <a href="#">🔗Link 2</a>
        <a href="#">🔗Link 3</a>
        <a href="#">🔗Link 4</a>
        <a href="#">🔗Link 5</a>
    </div>
```
div后面可以跟class也可以跟id，当它们被设置好后，你可以输入以下来快速得到内容：

假如你已经有 `<div class="nav">` 和 `<div id="nav">`

- 输入 `.nav` 以获得 `<div class="nav">`
- 输入 `#nav` 以获得 `<div id="nav">`

### `<span>`
span 是一个常用的行内标签，用于将特定的文本或其他行内元素分组，以便应用样式或进行操作。它本身不会改变内容的视觉效果，但在需要时可以与 CSS 或 JavaScript 配合使用。主要作用
1.	样式分组：可以对 <span> 包裹的内容应用单独的 CSS 样式，例如颜色、字体大小等。
```html
<p>这是一个 <span style="color: red;">红色</span> 的文字。</p>
```
2. JavaScript 操作：通过为 <span> 元素添加 id 或 class，可以让 JavaScript 选择和操作特定内容。
```html
<span id="highlight">点击我</span>

<script>
    document.getElementById("highlight").onclick = function() {
        alert("你点击了我！");
    };
</script>
```
3. 内联分组：在不影响文档布局的情况下，将文本或行内元素分组，适用于标题、段落等场景。
```html
<p>使用 <span class="important">span 标签</span> 可以为文本添加样式或交互。</p>
```
`<span>`是行内元素，通常用于小范围的内容分组；如果需要块级元素的效果，使用`<div>`更合适。

## HTML的表单
网页中允许用户进行输入（选择本质上也是输入）的地方（e.g.搜索栏），其本质就是HTML表单。创建一个表单和创建一个表格的语法类似。

### 一般输入
```html
<form>
    <!--placeholde使搜索框内有提示用户的文字-->
    <input type = "input" placeholder = "请输入内容">

    <!--value使搜索框内有提示用户的文字,且为输入的默认值-->
    <input type = "input" value = "请输入内容">
</form>
```
label标签可以用于提示输入框的信息，label标签可以带上 for 属性以和输入框绑定，通常情况下，我们要求 for 后面的内容和 input 标签的 id 属性的内容一致。


示例：登录界面输入密码
```html
<div>
    <form>
        <label for = "usrname" >Login ID: </label>
        <input type = "input" id = "usrname" placeholder = "Login ID">
        <br><br>
        <label for = "psswrd">Password: </label>
        <input type = "input" id = "psswrd" placeholder = "Password">
    </form>
</div>
```
<div>
    <form>
        <label for = "usrname" >Login ID: </label>
        <input type = "input" id = "usrname" placeholder = "Login ID">
        <br><br>
        <label for = "psswrd">Password: </label>
        <input type = "input" id = "psswrd" placeholder = "Password">
    </form>
</div>
当输入的为密码时，可以将 input type 改为 password 以实现隐藏输入内容的作用。

```html
<input type = "password">
```
<label>Hidden Passward: </label>
<input type = "password">

### 勾选输入
**单选** radio
```html
<input type = "radio" name = "gender">
```
**多选** checkbox
```html
<input type = "checkbox" name = "hobby">
```
示例：用户性别和喜好
```html
<form>
   <label>Gender: </lable>
   <input type = "radio" name = "gender"> Male
   <input type = "radio" name = "gender"> Female
   <input type = "radio" name = "gender"> Non-binary
   <br><br>
   <label>Hobbies: </lable>
   <input type = "checkbox" name = "hobby"> Sing
   <input type = "checkbox" name = "hobby"> Dance
   <input type = "checkbox" name = "hobby"> Rap
   <input type = "checkbox" name = "hobby"> Basketball
   <input type = "checkbox" name = "hobby"> Music
</form>
```
**不要忘记 name 属性！否则单选性质会失效！**
<form>
   <label>Gender: </lable>
   <input type = "radio" name = "gender"> Male
   <input type = "radio" name = "gender"> Female
   <input type = "radio" name = "gender"> Non-binary
   <br><br>
   <label>Hobbies: </lable>
   <input type = "checkbox" name = "hobby"> Sing
   <input type = "checkbox" name = "hobby"> Dance
   <input type = "checkbox" name = "hobby"> Rap
   <input type = "checkbox" name = "hobby"> Basketball
   <input type = "checkbox" name = "hobby"> Music
</form>

## 提交输入
form 标签有 action 属性 `<form action = "#">`, action里的内容应为某URL，其为后端所提供的API链接。
```html
<form action="#">
    <input type = "submit">
<form>
```
<form action="#">
    <input type = "submit">
<form>