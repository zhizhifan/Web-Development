# HTML 和 CSS 笔记

[toc]

## 前置知识

1. 前端和后端开发（front-end，back-end）。
2. 在前端开发中的三种语言：HTML 负责页面的内容（content），CSS 负责内容的呈现（presentation），JavaScript 则是真正的编程语言，负责添加动态和页面的交互（dynamic effects and web applications）
3. 开发者工具（DevTools）

## HTML（HyperText Markup Language）

我们使用 HTML 来构建页面内容，它包括了不同类型的元素，例如：**paragraphs, links, headings, images, video**等等。

### HTML 结构

#### 文档类型（Doc Type）

我们需要在 HTMl 开头进行文档声明：告诉浏览器当前文档使用的标准是 HTML5，浏览器会据此来进行规范的渲染。如果不声明的话文档会进入*怪异*的渲染模式：

```html
<!DOCTYPE html>
```

#### 根元素（html element）

```html
<html lang="en"></html>
```

- 一个界面最多一个，且该元素为父元素或者祖先元素。HTML 中没有强制要求书写该元素。
  - 其中的 `lang`属性为全局属性，表示该元素内部使用的文字是由哪一种自然语言书写而成的。如中文为：`cmn-hans`

#### 头部元素（head element）

文档头内部的内容，它包括了页面上有用的信息，且不会显示到页面上：

```html
<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Document</title>
</head>
```

- meta 元素指定元素据，其也为特殊的元素，没有结束标签。它的 `charset`属性指定网页内容编码。

#### 身体元素（body element）

页面上所有要参与的元素，都应该放置其中。它们将在页面中展现：

```html
<body></body>
```

### 语义化（semantic）

每个 HTML 元素都有具体的含义，如：

- a：超链接
- p：段落
- h：\*级标题

而所有的元素的展示效果与元素本身都没有关系，是由 css 语言决定的。
**所以选择元素只是基于元素本身的含义，而不是效果**。

### 注释书写格式

HTML 中的注释可以这样写：

```html
<!-- this is the test -->
```

### 实体字符（HTML Enitity）

用于在页面中显示一些特殊符号通常有两种写法：

1. &单词
2. &#数字

   ```html
   < 小于号 → 右箭头   空格号 nom-breaking space © 版权号 ¾ 四分之三 & &符号本身
   ```

另外可以通过该网址：[webpage here]() 进行更多实体字符的查找。

### 路径的写法

#### 站内资源和站外资源

站内资源：当前网站的资源(自己的)

站外资源：非当前网站的资源

#### 绝对路径和相对路径

站外资源：绝对路径

站内资源：相对路径

1. 绝对路径

   绝对路径的书写格式：（URL）

   ```html
   <!-- 协议名://主机名:端口号/路径 -->

   schema://host:port/path
   ```

   协议名:https,http,file(本地文件打开)
   主机名:域名，IP 地址(http://127.0.0.1:5500/index.html)
   端口号:如果协议名为 http，端口号为 80，https 协议名为 443

   当跳转目标和当前页面的协议相同时，可以省略协议

2. 相对路径

   以 `./`开头，`./`表示当前资源所在的目录，它可以省略

   ```html
   <a href="./test.html"></a> <a href="test.html"></a>
   ```

   以 `../`开头，表示返回上一级目录：

   ```html
   <a href="../test.html"></a>
   ```

### 元素

又称标签，标记，形如：

```html
<title>Document</title>
```

#### 基本定义

- 元素的构成：
  起始标记（opening/begin tag)）+ 内容（可以是文字，子元素或者空） + 结束标记（closing/end tag）+ 元素属性

属性:属性名 + 属性值
属性分类：局部属性(某些元素特有的属性) + 全局属性(所有元素共有的属性)

有些元素没有结束标记，这些元素叫做：**空元素**

```html
<meta charset="UTF-8" />
```

#### 元素的嵌套

元素不能互相嵌套

父元素，子元素，祖先元素，后代元素，兄弟元素(拥有同一个父元素)

#### 文本元素

1. h（标题）

   ```html
   (h$>{$级标题})*6 接着按tab键自动生成
   ```

   同时整个页面最好只有一个 h1 标题。

2. p（段落）

   在段落中添加文本时，可以对部分文字进行加粗和斜体处理

   ```html
   <p>this is the <strong>bold effect</strong></p>
   <p>
     this is the <em>italic effect</em>
     <!-- emphasize -->
   </p>
   ```

(3)span
没有语义，仅用于设置样式
如：
这个元素的颜色是:`<span style="color: red">`红

(4)pre
预格式化文本元素
空白折叠：在源代码中的连续空白字符(空格、换行、制表)，在页面显示时，会被折叠成一个空格
但在 pre 元素中的内容不会出现空白折叠，会直接按照源代码的格式显示到页面上
pre 元素的本质其实就是因为它有一个默认的 css 属性

```html
<body>
  <code>
    <pre></pre>
  </code>
</body>
```

#### 图片元素

img 元素（image）

img 元素比较特殊，它本身不需要任何内容，也没有结束标签（只需要一个 `/`），它的指定需要利用元素的一些属性，例如：

- src（source）：资源的路径。
- alt（alternative text）：当图片资源失效时，将使用该属性的文字替代图片。
- title：鼠标滑过图片时显示的文本。
- width，height：指定图片的宽高。

  ```html
  <img src="test.png" alt="HTML code on the screen" width="500" height="200" />
  ```

  但我们实际上很少直接在 `<img/>`里面指定图片的宽高，而是直接使用 css 样式。

- 和 a 元素联用

```html
<a href="https://bilibili.com">
  <img
    src="https://tse2-mm.cn.bing.net/th/id/OIP-C.5VSwpGRNrnryV2SMTTtLOAAAAA?w=179&h=180&c=7&r=0&o=5&pid=1.7"
    alt=""
    title=""
  />
</a>
```

- 和 map 元素

map：地图

map 的子元素：area

衡量坐标时，为了避免衡量误差，需要使用专业的衡量工具：ps、pxcook

```html
<body>
  <a
    href="https://baike.baidu.com/item/%E5%A4%AA%E9%98%B3%E7%B3%BB/173281"
    targrt="_blank"
  >
    <img usemap="#solar_image" src="./solar.jpg" alt="太阳系" />
  </a>
  <map name="solar_image">
    <area
      shape="circle"
      coords="360,204,48"
      href="https://baike.baidu.com/item/%E6%9C%A8%E6%98%9F/222105?fromModule=lemma_search-box"
      alt=""
      target="_blank"
    />
    <area
      shape="rect"
      coords="323,282,395,320"
      href="https://baike.baidu.com/item/%E6%9C%A8%E6%98%9F/222105?fromModule=lemma_search-box"
      alt=""
      target="_blank"
    />
    <area shape="poly" coords="" href="" alt="" /> #多边形
  </map>
</body>
```

其中：circle 的 coords 为圆心的坐标以及直径的坐标，rect 的 coords 为左上角和右下角的坐标，poly 的 coords 为每个点的坐标

- 和 figure 元素

指代、定义，通常用于把图片、图片标题、描述包裹起来
子元素：figcaption,通常包裹里面的标题

```html
<figure>
  <a
    href="https://baike.baidu.com/item/%E5%A4%AA%E9%98%B3%E7%B3%BB/173281"
    targrt="_blank"
  >
    <img src="./solar.jpg" alt="太阳系" />
  </a>
  <figcaption>
    <h2>太阳系</h2>
  </figcaption>
  <p>太阳系是.....</p>
</figure>
```

#### 链接元素

a 元素（anchor）

content 内容部分的文本是对应链接上显示的文字。a 元素的属性包括：

1. href（hyper reference）：

   真正使得 a 元素称为链接的原因是 `href`属性，如果不指定属性，则只是没有作用的一段文字。根据 href 属性的指定形式，有如下几种功能：

   - URL

     ```html
     <a href="https://www.baidu.com/"> Baidu </a>

     <a href="Blog.html">
       <!-- link to another page in the project -->
       Another page
     </a>
     ```

   - 锚链接

     链接到页面的特殊部分：

     ```html
     <a href="#"> return to the top of the page </a>
    
     <a href="#chapter1"> Chapter1 </a>
     <h2 id="chapter1">章节1</h2>
     <p>Lorem ipsum dolor</p>
     ```

     id 属性：全局属性，表示属性在文档中的唯一编号

2. 功能链接(点击后，触发某个功能)
   执行 JS 代码，javascript:
   发送邮件，mailto: 要求用户计算机上安装有邮件发送软件：exchange
   拨号，tel: 要求用户计算机上安装有拨号软件，或使用的是移动端访问
3. target：

   表示跳转窗口位置。它的取值包括：

   - \_self：在当前页面窗口中打开，默认值。
   - \_blank：在新页面窗口中打开。

   ```html
   <p>
     Open this page at
     <a href="https://www.baidu.com/" target="_blank"> Baidu </a>
   </p>
   ```

4. title：
   全局属性，光标浮于链接上显示的信息

   ```html
   <a href="https://bilibili.com" target="_blank" title="哔哩哔哩干杯！">
     BiliBili
   </a>
   ```

#### 多媒体元素

1. video

- controls: 布尔属性，控制控件的显示，取值只能为 controls
- autoplay: 布尔属性，自动播放。
- muted: 布尔属性，静音播放。
- loop: 布尔属性，循环播放

```html
<video controls autoplay muted loop src=""></video>
```

**某些属性，只有两种状态：1. 不写 2. 取值为属性名。 这种属性叫做布尔属性**

布尔属性，在 HTML5 中，可以不用书写属性值

2. audio

   知识和 video 完全一致

#### 兼容性

1. 旧版本的浏览器不支持这两个元素
2. 不同的浏览器支持的音视频格式可能不一致

mp4、webm,为了保证兼容性，可以按照如下方式改进代码

```html
<video controls autoplay muted style="width:500px">
  <source src="./open.mp4" />
  <source src="./open.webm" />
</video>
```

#### 列表元素

1. 有序列表（ordered list）

   利用 `ol`元素和 `li`（list item）元素。

   ```html
   <body>
     How should I do this thing?
     <ol>
       <li>step1</li>
       <li>step2</li>
       <li>step3</li>
     </ol>
   </body>
   ```

2. 无序列表（unordered list）

   ```html
   <body>
       How should I do this thing?
       <ul>
           <li>
               step1
           </li>
           <li>
               step2
           </li>
           <li>
               step3
           </li>
       </ol>
   </body>
   ```

3. 定义列表

   通常用于一些术语的定义

   dl: definition list

   dt: definition title

   dd: definition description

```html
<dl>
  <dt>标题五个字</dt>
  <dd>这段话的含义是.....</dd>
</dl>
```

列表属性：

1. `list-style`

ol 属性 type,取值为 1：列表以数字排列；取值为 i：列表以罗马数字排列；取值为 a(A)，以字母排列(不建议用 type，除非特殊情况)。

#### 按钮元素

#### 容器元素

容器元素：该元素代表一个块区域，内部用于放置其他元素。在语义化 HTML 出现以前，通常直接用 `<div></div>`

1. nav（navigation）：通常表示导航栏。

   ```html
   <nav>
     <a href="page1.html">Page 1</a>
     <a href="page2.html">Page 2</a>
   </nav>
   ```

2. header：通常用于表示页头，也可以用于表示文章的头部。
3. footer: 通常用于表示页脚，也可以用于表示文章的尾部。
4. section: 通常用于表示文章的章节。
5. article：通常用于表示整篇文章。

   ```html
   <article>
     <header></header>
     <section></section>
     <footer></footer>
   </article>
   <!-- it seems more logical -->
   ```

6. aside: 通常用于表示侧边栏，是一些次要或补充信息。

### 元素包含关系

以前：块级元素可以包含行级元素，行级元素不可以包含块级元素，a 元素除外

元素的包含关系由元素的内容类别决定。

例如，查看 h1 元素中是否可以包含 p 元素(显然不可以，因为一级标题无法包含段落)：**h1 mdn**

总结：

1. 容器元素中可以包含任何元素
2. a 元素中几乎可以包含任何元素
3. 某些元素有固定的子元素
4. 标题元素和段落元素不能相互嵌套，并且不能包含容器元素

## CSS（Cascading Style Sheet）

CSS 包括很多属性，这些属性允许我们对已有的 HTML 进行内容的格式化，如字体，页面布局等等。

### 术语解释

**CSS 规则 = 选择器（selector）+ 声明块（declaration block)（property + value）**

### CSS 代码书写位置

1. 内联样式表（inline CSS）[不推荐]

   直接书写在元素的 `style`属性中：

   ```css
   <p style="color:blue">
       Blue header
   </p>
   ```

2. 内部样式表（internal CSS）

   书写在 `head`元素的 style 元素中：

   ```html
   <!-- element selector -->
   <head>
     <style>
       h1 {
         color: blue;
       }
     </style>
   </head>
   ```

3. 外部样式表（external CSS）[推荐]

   将样式书写到独立的 CSS 文件中：

   ```css
   /* CSS文件的注释要这么写 */
   h1 {
     color: blue;
   }
   ```

   ```html
   <!-- link the CSS file -->
   <head>
     <link rel="stylesheet" href="style.css" />
   </head>
   ```

> 1. 外部样式可以解决多页面样式重复的问题。
> 2. 有利于浏览器缓存，从而提高页面响应速度。
> 3. 有利于代码分离（HTML 和 CSS），更容易阅读和维护。

### 选择器

#### 选择器类型

1. ID 选择器（ID selector）

   选中的是对应 id 值的元素，每个元素都可以设置一个独立的 `id`属性：

   ```html
   <p id="demo">This is an example</p>
   ```

   ```css
   #demo {
     font-family: sans-serif;
   }
   ```

2. 元素选择器（element selector）

   对所有的同一元素进行选择修改：

   ```html
   <head>
     h1{ color:red; background-color:lightblue; text-align: center; }
   </head>
   ```

3. **类选择器（class selector）**[推荐]

   由于每个 id 只能使用一次，所以在某种情况下 class 会是一个更好的选择，这是为未来代码维护而准备的：

   ```html
   <p class="class1">This is an example</p>
   ```

   ```css
   .class1 {
     font-size: 26px;
   }
   ```

#### 选择器扩展

1. ID 选择器
2. 元素选择器
3. 类选择器
4. 通用选择器（universal selector）

   `*`会选中所有元素（head, body, html 和其中的元素都会被选中并改变样式）

   ```css
   * {
     font-family: sans-serif;
   }
   ```

5. 属性选择器

   根据属性名和属性值选中元素(了解，自己去 mdn 上搜)

6. **伪类选择器（pseudo class）**

   - 选择某些元素的某种状态（一般用来 styling hyperlink）

     1. `a:link `超链接未访问时的状态（注意，这里选择的 a 元素一定是有 `href`属性的）

        ```css
        a:link {
          color: red;
        }
        ```

     2. `a:visited`超链接访问过后的状态

        ```css
        a:visited {
          color: #f7f7f7;
        }
        ```

     3. `a:hover`: 鼠标悬停状态

        ```css
        a:hover {
          color: orangered;
          font-weight: bold;
        }
        ```

     4. `a:active`：激活状态，鼠标按下状态

        ```css
        a:activate {
          font-style: italic;
        }
        ```

   - 选择文档中不能通过其他选择器选择的元素（这些元素没有 ID 或 class 属性）

     ```css
     li:first-child {
       font-weight: bold;
     }
     /* 匹配所有li元素父元素的第一个li元素*/
    
     ul li:last-child {
       font-style: italic;
     }
     /* 匹配所有ul元素的第一个li元素*/
    
     li:nth-child {
       font-color: red;
     }
     ```

7. 伪元素选择器

before

after(相当于在元素前/后面添加内容和样式)

```css
<head>
  <style>
        span::before{
            content:'《';
                color: red;
            }
        span::after{
            content:'》';
                color: red;
        }
    </style>
</head>
<body>
    <p>
       <span>老人与海</span>是一本好书
    </p>
</body>
```

#### 选择器的组合（combining selectors）

1. 列表选择器（list selector）

   多个选择器之间用逗号分隔，可以达到多个选择的目的：

   ```css
   h1,
   h2,
   p {
     font-family: sans-serif;
   }
   ```

2. 后代选择器（descendant selector）

   用空格连接，连接的对象可以是类（`.class`)，也可以是元素名,或者是其他，只要是选择器即可。后代选择器是为了进一步细致的选择和改变：

   ```css
   /* nest it, but it is too complicated */
   article footer p {
     font-size: 15px;
   }
   =========================================== article .title {
     color: red;
   }
   ```

   子元素 —— >

3. **相邻**的兄弟元素 —— +
4. 后面出现的所有兄弟元素 —— ~

### 声明块

出现在大括号中

声明块中包含很多声明（属性），每一个声明（属性）表达了某一方面的样式。

#### 常见样式声明

1. `color`

   元素内部的文字颜色(有如下两种情况)

   - 预设值：具有意义的，已经定义好的颜色单词。
   - RGB 表示法（RGB notation）

     - `rgb()`
     - `rgba()` _a 表示 alpha 透明度_

   - 十六进制表示法（Hexadecimal notation）

     ```css
     h1 {
       color: #00ffff;
       /* color:rgb(0, 255, 255) */
     }
     ```

     此外我们知道 rgb(0, 0, 0)代表黑色，rgb(255, 255, 255)代表白色。为了表示灰色，我们需要使得红绿蓝三个通道的值保持一致，值的不同代表了灰度的不同。

2. background-color

   元素背景颜色

   ```css
   header {
     background-color: #f7f7f7;
   }
   ```

3. font-size

   元素内部文字的尺寸大小

   - `px`：像素，绝对单位，简单的理解为文字的高度占多少个像素
   - em：相对单位，相对于父元素的字体大小
     **每个元素必须有字体大小，如果没有声明，则直接使用父元素的字体大小，如果没有父元素（html），则使用基准字号(浏览器自动设置的大小)。**

> user agent，UA，用户代理（浏览器）-----user agent stylesheet

4. font-weight

   文字粗细程度，可以取值数字，可以取值为预设值(normal:400,bold:700)：

   ```css
   p {
     font-weight: bold;
   }
   ```

> strong 默认加粗。
> strong 元素表示重要的，不能忽略的内容

5. font-family

   文字类型，必须在**用户计算机中**也存在相同的字体时才会有效。为了防止冲突，可以使用多个字体，以匹配不同环境

   ```css
   h1{
       font-family:sans-serif;
   }


   <style>
       font-family:微软雅黑,翩翩体-简,Arial, Helvetica, sans-serif;(sans-serif，通用字体--非衬线字体)
   </style>
   ```

6. font-style

   字体样式，通常用它设置斜体：

   ```css
   h1 {
     font-style: italic;
   }
   ```

7. text-transform

   转换成大写，小写等：

   ```css
   h1 {
     text-transform: lowercase;
   }
   ```

> i 元素，em 元素，默认样式，是倾斜字体; 实际使用中，通常用 i 表示一个图标（icon）；em 元素表示强调的内容

7. text-align

   就像在 MS Word 中一样的文字对齐：`left/right/center`：

   ```css
   h1 {
     text-align: center;
   }
   ```

8. text-decoration

   文本修饰，可以选择给文本加线。同样的，该样式可以同时接受多个属性的声明

   ```css
   a:link {
     text-decoration: underline dotted orangered;
   }
   ```

9. text-indent

首行文本缩进
可以用像素值，或者 em

10. line-height

    每行文本的绝对高度，该值越大，每行文本的距离越大。可以认为行高是字体大小的 x 倍

    ```css
    p {
      lineheight: 1.5;
    }
    ```

设置行高为容器的高度，可以让单行文本垂直居中

```css
<head>
    <style>
        p{
            background-color: rgb(75,144,128);
            color: white;
            font-family:Arial, Helvetica, sans-serif;
            height: 50px;
            line-height: 50px;
        }
    </style>
</head>
<body>
    <p>
        Lorem ipsum dolor sit amet.
    </p>
```

行高可以设置为纯数字，表示相对于当前元素的字体大小

```css
line-height: 1.5;
```

11. border

    border 可以为一些容器添加边框属性。该样式的一个特点就是可以接受多个值：

    ```css
    nav {
        border: 5px solid #1098ad;
        /* border width, border style, border color
    }
    ```

    > 此外还有一些 border 的变体，例如 border-top, border-left 等。

---

### <font color="red">层叠</font>

**声明冲突：同一个样式，多次应用到同一个元素**

我们在一次 HTML，CSS 文件的编写过程中可能常常会有疑惑，当我们多次应用 CSS 样式到同一个元素时，究竟哪个样式会得到声明，例如：

```html
<p id="author-text" class="author">this is a paragraph</p>
```

```css
.author {
  font-style: italic;
  font-size: 18px;
}

#author-text {
  font-size: 20px;
}

p {
  font-family: sans-serif;
  color: "red";
  font-size: 22px;
}

/* which size will be applied? */
```

层叠：解决声明冲突的过程，浏览器自动处理（权重计算）

#### 比较重要性

重要性从高到底：

> 作者样式表：开发者书写的样式

1. 作者样式表中的 `!important`样式（最重要的级别，一般不推荐使用）

   ```css
   p {
     color: red !important;
   }
   ```

2. 作者样式表中的普通样式
3. 浏览器默认样式表中的样式

#### 比较特殊性(重要性相同的情况下，冲突仍然存在，进行特殊性比较)（Selector Specificity）

- 看选择器
  - 总体规则：选择器选中的范围越窄，越特殊。简单来说，如果存在多个选择器且*冲突存在*的情况下，id 选择器，（伪）类选择器，元素选择器，通用选择器依次优先。若同时存在多个相同选择器，则最后一个选择器优先。
  - 具体规则：上述只是一个简单的概述，我们通过选择器，计算出一个 4 位数（x x x x）

1. 千位：如果是内联样式，记 1，否则记 0
2. 百位：等于选择器中所有 id 选择器的数量
3. 十位：等于选择器中所有类选择器、属性选择器、伪类选择器的数量
4. 个位：等于选择器中所有元素选择器、伪元素选择器的数量

```css
    <style>
        a{
            color: red;
        }
        div ul a{
            color: green;
        }
        #mydiv #myul a{
            color: gray;
        }
        #mydiv #myul .mylink{
            color: aqua;
        }
        #mydiv #myul a:link{
            color: blue;
        }
    </style>
</head>
<body>
    <div id="mydiv">
        <ul id="myul">
            <li id="myli">
                <a href="" id="mylink">
                </a>
            </li>
        </ul>
```

#### 3. 比较源次序

代码书写靠后的胜出

#### 应用

1. 重置样式表

书写一些作者样式，覆盖浏览器的默认样式

重置样式表 -> 重置浏览器的默认样式

常见的重置样式表：normalize.css、reset.css、meyer.css

2. 爱恨法则

link > visited > hover > active(其实是按照源次序排列的)

### `<font color="red">`继承`</font>`

子元素会继承父元素的某些 CSS 属性。通常，只有跟文字内容相关的属性才能被继承。当然继承的样式也很容易被覆盖掉。

```html
<body>
  <nav>this is the navigation</nav>
  <h1>My website</h1>
  <p>the text is this paragraph is completely irrelevant</p>
</body>
```

```css
body {
  color: #444;
  font-size: 16px;
  font-family: sans-serif;
  border-top: 10px solid #1095cd;
}
```

通过 `mdn`查询哪些属性会被继承。

### 简写属性

- 语法糖
  font 简写属性

margin 简写属性：margin x y (s 上下/左右)

border 简写属性:border width style color

### 属性值的计算过程

一个元素一个元素依次渲染，顺序按照页面文档的树形目录结构进行

![](/2019-05-17-12-27-14.png)

渲染每个元素的前提条件：该元素的**所有 CSS 属性**必须有值

一个元素，从所有属性都没有值，到所有的属性都有值，这个计算过程，叫做属性值计算过程

属性值计算过程简介：

1. 确定声明值：参考样式表中(作者样式表，浏览器样式表)没有冲突的声明，作为 css 属性值
2. 层叠冲突：对样式表中有冲突的声明使用层叠规则，确定 css 属性值
3. 使用继承：**对仍然没有值的属性**，若可以继承，则继承父元素的值(已经有值的不会继承)
4. 使用默认值：对仍然没有值的属性，使用默认值

特殊的两个 CSS 取值：

- inherit：手动（强制）继承，将父元素的值**取出应用到该元素**

```css
color: inherit;
```

- initial：初始值，将该属性设置为默认值

### <font color='red'>盒模型</font>（box model）

盒模型，意味着每个元素在页面中都会生成一个矩形区域（盒子）。

盒子类型分为三种：

1. **行盒**（inline-level boxes)，`display`属性等于`inline`的元素
2. **块盒**（block-level boxes)，`display`属性等于`block`的元素
3. **行块盒**，`display`属性等于`inline-block`的元素

块盒占据了父元素宽度的100%，不管它们的内容多少。如果内容很多会换行，如果内容不多仍是原样。这使得块盒永远独占一行，不能并排放置。

默认的块盒有：`容器元素`、`body`、`h1~h6`、`p`、`ul`、`ol`、`li`

行盒则取决于它们内容的多少。内容很多的话也不会进行换行，因而它们适合较小元素。==对于行盒来说宽度和高度都没有用，并且paddings和margins也只在水平方向上有用==。

常见的行盒：`strong`、`em`、`span`、`a`、`img`、`video`、`audio`、`button`

行块盒从外面看是行盒，从内部表现却是块盒。它们取决于内容的宽度，不会导致换行符，因而不独占一行，仍在一行中。但盒模型中所有尺寸以及paddings、margins都适用于行块盒。

其实`img`元素表现的类似行块盒，这与其他行盒不同。不然它也不能设置宽高。

![box-model](D:\Learning Materials\前端\notes\images\css-boxmodel.png)

![width and height](D:\Learning Materials\前端\notes\images\calculating widthheight.png)

如上图所示，无论是行盒、还是块盒，都会由下面几个部分组成：

1. 内容（content）

   内容部分通常叫做整个盒子的**内容盒（content-box）**

   `width`和 `height`，设置的是盒子内容的宽和高，或者直接说内容盒的宽高。

   在设置图片的宽高的时候，我们往往只会设置图片的**宽**，然后将高度设置为 `auto`，这样做不会压缩图片，仍使其保持原比例。

   ```css
   img {
       width: 100%;	/* 百分比格式是指占据父容器宽度的百分数
       height: auto
   }
   ```

2. 填充(内边距) （padding）

   盒子边框到盒子内容的距离。

   可以依次指定样式：`padding-left`、`padding-right`、`padding-top`、`padding-bottom`（左右上下边距，默认为 0）。也可以直接使用 padding 的简写属性： padding: top right bottom left（按照顺时针）。

   ```css
   h1 {
     padding: 20px; /* all the direction */
     padding: 20px 40px; /* top, bottom = 20px, left and right = 40px */
   }
   ```

   填充区+内容区 = **填充盒 padding-box**

3. 边框 border

   边框 = 边框样式 + 边框宽度 + 边框颜色

   边框样式：border-style

   默认为 none，常见的样式有 solid(实线边框)

   边框宽度：border-width

   边框颜色：border-color

   默认按照字体颜色设置

   设置圆角边框: border-radius

   **border-style(width,color)都是简写属性，也可以通过上右下左来设置**

   边框+填充区+内容区 = **边框盒 border-box**

4. 外边距（margin）

   边框到其他盒子的距离。margin-top、margin-left、margin-right、margin-bottom。简写属性 margin 和 padding 用法一致。一般我们在**设置垂直方向上元素之间的间距时**，会直接使用 `margin-bottom`。

   ```js
   li {
       margin-bottom: 10px;
   }
   li:last-child {
       margin-bottom: 0;
   }
   ```

   通常会在一开始重置所有 padding 和 margin 为 0：

   ```css
   * {
     padding: 0;
     margin: 0;
   }
   /* 使用通配符选择器 */
   ```

#### 块盒

块盒独占一行

#### 行盒

### 盒模型应用

#### 块盒

- 改变宽高范围

默认情况下，width 和 height 设置的是内容盒宽高。

> 页面重构师：将 psd 文件（设计稿）制作为静态页面

衡量设计稿尺寸的时候，往往使用的是边框盒的宽高，但如果设置 width 和 height 的值，其实设置的是内容盒

解决方案：

1. 精确计算
2. CSS3：box-sizing

```css
<style>
    div{
        width: 236px;
        height:20px;
        color: #a7a7a7;
        background-color: #2d2e36;
        box-sizing: border-box;        #将原本内容盒的宽高设置成边框盒的宽高
        line-height:40px
        }
</style>
```

- 改变背景覆盖范围

默认情况下，背景覆盖边框盒

可以通过 background-clip 进行修改

background-clip:content-box,padding-box,border-box

- 溢出处理

理论上需要在父元素的包含块里活动，但当发生溢出时，默认仍显示溢出部分的内容。

通常情况下会自动处理行高防止溢出

overflow，控制内容溢出边框盒后的处理方式

overflow:visiable
overflow:hidden #溢出隐藏
overflow:scroll(overflow-x/y:scroll)
overflow:auto #自动出现滚条

- 断词规则

word-break，会影响文字在什么位置被截断换行

normal：普通。CJK 字符（文字位置截断），非 CJK 字符（单词位置截断）

break-all：截断所有。所有字符都在文字处截断
word-break:break all

keep-all：保持所有。 所有文字都在**单词**之间截断
word-break:keep-all

- 空白处理

有时候不需要内容(没有溢出)进行换行-------->white-space: nowrap

```css
 <style>
    li{border-bottom: 1px dashed #ccc;
            line-height: 2;
            border-left: 3px solid #008c8c;
            margin:1em 0;
            width: 200px;
            white-space:nowrap;
            overflow: hidden;
            text-overflow: ellipsis;  #三个点替代
    }
</style>
```

#### 行盒的盒模型

常见的行盒：包含具体内容的元素

a、span、strong、em、i、img、video、audio

##### 显著特点

1. 盒子沿着内容沿伸
2. 行盒不能设置宽高

调整行盒的宽高，应该使用字体大小、行高、字体类型，间接调整。

3. 内边距（填充区）

水平方向有效，垂直方向不会实际占据空间。

4. 边框

水平方向有效，垂直方向不会实际占据空间。

5. 外边距

水平方向有效，垂直方向不会实际占据空间。

#### 行块盒

- 可以设置宽高

使用------>display：inline-block

1. 

#### 值得注意的一个小知识点:空白折叠

空白折叠，发生在行盒（行块盒）内部 或 行盒（行块盒）之间

#### 可替换元素 和 非可替换元素

大部分元素，页面上显示的结果，取决于元素**内容**，称为**非可替换元素**

少部分元素，页面上显示的结果，取决于元素**属性**，称为**可替换元素**

可替换元素,如：img、video、audio

**绝大部分可替换元素均为行盒。**

**可替换元素类似于行块盒，盒模型中所有尺寸都有效。**

### 视觉格式化模型

盒模型：规定单个盒子的规则

视觉格式化模型（布局规则）：页面中的多个盒子排列规则

视觉格式化模型，大体上将页面中盒子的排列分为三种方式：

1. 常规流
2. 浮动
3. 定位

#### 常规流布局

- 几种叫法：常规流、==文档流==、普通文档流、常规文档流
- 所有元素，默认情况下，都属于常规流布局
- 总体规则：块盒独占一行，行盒水平依次排列
- 包含块（containing block）：每个盒子都有它的包含块，包含块决定了盒子的排列区域。

绝大部分情况下：**盒子的包含块，为其父元素的内容盒**

**块盒**

1. 每个块盒的总宽度(content+padding+border)，必须刚好等于包含块的宽度(块盒必须占满)

宽度的默认值是 auto

margin 的取值也可以是 auto，**默认值 0**

auto：将剩余空间吸收掉

width 吸收能力强于 margin

若宽度、边框、内边距、外边距计算后，仍然有剩余空间，该剩余空间被 margin-right 全部吸收

**在常规流中，块盒在其包含块中居中，可以定宽(width)、然后左右 margin 设置为 auto。**

margin 可以设置为负值

2. 每个块盒垂直方向上的 auto 值

height:auto， **适应内容的高度**(此时，若包含块的高度也没有设置，则包含块的高度取决于块盒的高度)

margin:auto， 表示 0

3. 百分比取值

==padding、宽(width)、margin==可以取值为百分比

以上的所有百分比相对于包含块的**宽度**。

- 高度的百分比：

1）. 包含块的高度取决于子元素的高度，此时设置百分比无效
2）. 包含块的高度不取决于子元素的高度，百分比相对于**父元素**高度

4. **上下外边距的合并**

两个常规流块盒，上下外边距相邻(没有 border 进行隔开)，会进行合并。(两个外边距取最大值。)要时刻注意上下外边距的合并。

#### 浮动布局

##### 应用场景

1. 文字环绕
2. 横向排列

```css
<head>
    <style>
        .container{
            width:1000px;
            height:500px;
            background:lightblue;
        }
        .container .item{
            width: 50px;
            height: 50px;
            background-color: red;
            border: 2px dashed black ;
            color: #fff;
            font-style: italic;
            font-size: 2em;
            float:left
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
    </div>
</body>
```

##### 浮动的基本特点

只要修改 float 属性值为：

- left：左浮动，元素靠上靠左
- right：右浮动，元素靠上靠右

float 默认值为 none，即为常规流

> 当一个元素浮动后，==元素必定为块盒==(即更改 display 属性为 block)
> 浮动元素的包含块，和常规流一样，为父元素的内容盒

##### 盒子尺寸

1. ==宽度为 auto 时，适应内容宽度==
2. ==高度为 auto 时，与常规流一致，适应内容的高度==
3. == 若 margin 为 auto，为 0.==
4. 边框、内边距、百分比设置与常规流一样

##### 盒子排列

1. 左浮动的盒子靠上靠左排列
2. 右浮动的盒子考上靠右排列
3. 浮动盒子在包含块中排列时，会避开常规流块盒(即已经先排列了常规流块盒，再排浮动流的情形)
4. 常规流块盒在排列时，无视浮动盒子(即已经先排列浮动流，再排列常规流块盒的情形)
5. ==*行盒*在排列时，会避开*浮动盒子*==(文字环绕的应用)

```css
<body>
    <img src="/solar.jpg" alt="" style="float:left;margin-right:10px">
    <p>xxxxxxx</p>
</body>
```

> ==如果文字没有在行盒中，浏览器会自动生成一个行盒包裹文字，该行盒叫做匿名行盒。==
> 而行盒会自动避开浮动盒，因而形成一种文字环绕的效果。
> **此外还可以设置浮动盒的 margin-来设置浮动间距。**

6. 外边距合并不会发生

##### 高度坍塌

高度坍塌的根源：常规流盒子的自动高度(auto---自动适应高度)在计算时，不会考虑浮动盒子。因而会出现高度坍塌现象，此时设置常规流盒的高度为固定值则会避免此现象。

```css
<head>
  <style>
        .container{
            padding:30px;
            background:lightblue;
        }
        .container .item{
            background:red;
            margin:2px;
            width: 100px;
            height:100px;
            float:left;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
    </div>
<body>
```

##### 清除浮动

==涉及 css 属性：clear==

- 默认值：none
- left：清除左浮动，该元素必须出现在前面所有左浮动盒子的下方
- right：清除右浮动，该元素必须出现在前面所有右浮动盒子的下方
- both：清除左右浮动，该元素必须出现在前面所有浮动盒子的下方

这样做可以解决高度坍塌：

```css
<head>
  <style>
        .container{
            padding:30px;
            background:lightblue;
        }
        .container .item{
            background:red;
            margin:2px;
            width: 100px;
            height:100px;
            float:left;
        }
        .container .clearfix{
            height: 100px;
            clear:both;
            background:blue;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="clearfix"></div>
    </div>
<body>
----------------------------------或者
<head>
  <style>
        .container{
            padding:30px;
            background:lightblue;
        }
        .container .item{
            background:red;
            margin:2px;
            width: 100px;
            height:100px;
            float:left;
        }
        .clearfix::after{
           content:'';
           display:block;
           clear:both;
        }
    </style>
</head>
<body>
    <div class="container clearfix">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="clearfix"></div>
    </div>
<body>
```

#### 定位

定位：手动控制元素在包含块中的精准位置

涉及的 CSS 属性：position

##### position 属性

- 默认值：static，静态定位（即不定位）
- relative：相对定位
- absolute：绝对定位
- fixed：固定定位

一个元素，只要 position 的取值不是 static，认为该元素是一个定位元素。

定位元素会脱离文档流（即常规流）（相对定位除外）

一个脱离了文档流的元素：

1. 文档流中的元素摆放时，会忽略脱离了文档流的元素
2. 文档流中元素计算自动高度时，会忽略脱离了文档流的元素

##### 相对定位

- 不会导致元素脱离文档流，只是让元素在原来位置上进行偏移,不会让元素进行压缩（与调整 margin 不同）
- 常常用于为绝对定位提供包含块

可以通过四个 CSS 属性对设置其位置：

- left
- right
- top
- bottom

  **尽量避免冲突设置，如果发生设置冲突：上下冲突时看上，左右冲突时看左**

```css
<head>
    <style>
        .item{
            background:red;
            border: 1px black solid;
            height:50px;
        }
    </style>
</head>
<body>
    <div class="item"></div>
    <div class="item" style="position:relative;right:50px"></div>
    <div class="item"></div>
<body>
```

==盒子的偏移不会对其他盒子造成任何影响。==

##### 绝对定位

1. 宽高为 auto，适应内容
2. ==包含块变化：找祖先中**第一个**定位元素，该元素的**填充盒为其包含块**。若找不到，则它的包含块为整个网页（初始化包含块）==
3. 设置 left,right,top,bottom:距离其包含块的距离(即祖先元素中第一个定位元素的填充盒,或者初始化包含块)
4. 常常用于图片的重叠

##### 固定定位

其他情况和绝对定位完全一样。

但与绝对定位不同的是包含块：固定定位的包含块固定为视口（浏览器的可视窗口）

> 整个网页与视口不是同一个概念，若整个网页大于视口，会出现滚动条。此时设置固定定位，该原素不会随着滚动条的拖动而改变位置(广告的应用)

##### 定位下的居中

```html
<div class="container">
  <h1>header1</h1>
  <p>paragraph1</p>
</div>
```

```css
.container {
    width: 700px;
    margin 0 auto;
}
```

==某个方向居中，步骤:==

1. ==定宽（高）==
2. ==将左右以及上下距离设置为 0==
3. ==将左右以及 margin 设置为 auto==
   绝对定位和固定定位中，margin 为 auto 时，会自动吸收剩余空间

```css
<head>
    <style>
        .item{
            background:red;
            border: 1px black solid;
            height:50px;
            position:fixed;
            width:100px;
            height:100px;
            right:0;
            left:0;
            top: 0;
            bottom:0;
            margin:auto;
        }
    </style>
</head>
<body>
    <div class="item"></div>
</body>
```

##### 多个定位元素重叠时

堆叠上下文(?)

设置 z-index，通常情况下，该值越大，越靠近用户（奥运五环）

只有定位元素设置 z-index 有效

z-index 可以是负数，如果是负数，若遇到常规流、浮动元素，则会被其覆盖

##### 补充

- 绝对定位、固定定位元素一定是**块盒**
- 绝对定位、固定定位元素**一定不是浮动**
- 没有外边距合并

### 应用(常见组件)

1. 菜单栏
2. 弹出层

# JavaScript 笔记

JavaScript 是一个高级的，面向对象的（object-oriented），多范式的（multi-paradigm）编程语言。

从最初的 ES5（ECMAScript）开始，2015 年迎来了该语言的最大更新，即 ES2015（ES6)，之后的版本更新都属于现代 JavaScript。

## 前置知识

1. JavaScript 是基于 HTML 文件的。
2. 变量和值。变量名一般采用驼峰式命名（camelCase）。声明变量并进行赋值的过程用 `let`：

   ```js
   let firstName = "Jonas";
   ```

   当再次给同一变量赋值时，无需再使用 `let`：

   ```js
   firstname = "Jone";
   ```

   也可分开书写，即先声明变量，再进行赋值：

   ```js
   let firstName;
   firstName = "Jonas";
   ```

   在声明常量时，我们使用 `const`，常量不可再次更改：

   ```js
   const birthYear = 2002;
   ```

   变量名的命名过程有一些规定：

   ```js
   let 3years = "hello";	/* 不能以数字开头 */
   let Jonas = "hello";	/* 不能以大写字母开头 */
   let $first_name1 = "hello";	/* 实际上，js命名只能包括$，字母，下划线和数字 */
   let a&b = "hello";		/* error */
   let new = "hello";		/* js中保留的关键字也不能用以命名 */
   ```

3. JavaScript 中的七种变量类型（Data Types），不需显示声明变量类型：

   1. 数字（used for decimals and integers）
   2. 字符串
   3. 布尔值
   4. 未定义（Undefined, value taken by a variable that is not yet defined）
   5. 空（Null，also means 'empty value'）
   6. 符号（Symbol（ES2015）,value that is unique and connot be changed）
   7. 大整型（BigInt）

      ```js
      console.log(typeof true);
      // 查看值类型
      ```

   值类型之间可以进行类型转换和类型强迫（type conversion and type coercion），类型转换是手动的，而类型强迫是 JavaScript 自动转换的（事实上这是更常见的）。

   - type conversion

     - 字符串转换为数字（`Number()`）

       ```js
       const inputYear = "1991";
       console.log(Number(inputYear) + 18);
       console.log(Number("Jonas"));
       // NaN --- it's still a number, but not a valid number
       ```

     - 数字转换成字符串（`String()`）

       ```js
       console.log(String(23));
       ```

     - 转换成布尔值（`Boolean()`）

       只有五个值在转换中被转换成 false：`0`，`''`，` undefined`，`null`，`NaN`，其余都会被转换成 true。

       ```js
       console.log(Boolean(0));
       console.log(Boolean({}));
       ```

   - type coercion

     - ```js
       console.log("I'm" + 28 + "years old")；
       // 加法将数字转换成字符串
       console.log("23" - 10)；
       // 减法，乘法，除法将字符串转换成数字
       ```
     - 布尔值的类型转换只会发生在以下两种类型：

       1. 使用逻辑运算符（logical operators）
       2. 在逻辑上下文中（logical context）

          ```js
          const money;
          if(money) {
              console.log("You have no money");
          } else {
              console.log("Get a job");
          }
          ```

4. JavaScript 中的运算符（operators）

   1. 数学运算符

      ```js
      const num = 23;
      console.log(num ** 2); // 乘幂
      ```

   2. typeof 运算符
   3. 赋值运算符

      ```js
      let x = 15;
      x += 10;
      x *= 2;
      x++; //x = x+1
      x--; //x = x-1
      console.log(x);
      ```

   4. 比较运算符

      在这里需要提一点相等运算符，我们应该使用 `===`，这表示这种相等是严格（strict）的，不存在类型强制。但如果使用 `==`，则是宽松的（loose），它允许类型强制。为了代码的可检查性，最好使用 `===`。

      ```js
      console.log("18" === 18);
      console.log("18" == 18);
      ```

      如果使用不等运算符，严格版本是 `!==`，宽松版本是 `!=`。

   5. 逻辑运算符

      1. `&&`：当所有变量都为真时，结果为真。
      2. `||`：当有一个变量为真时，结果为真。
      3. `!`：反转逻辑。

      ```js
      const conditionA = true;
      const conditionB = false;
      if (conditionA && conditionB) {
        console.log("This is the true answer");
      } else {
        console.log("The wrong answer");
      }
      ```

   6. 运算符优先级（operator precedence）

      mdn 中有详细的表格：[webpage here]([Operator precedence - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence))

5. Javascipt 字符串（模板字符串）（template literrals）

   ```js
   const allname = "zhizhifan";
   const age = 20;
   const writer = `I'm ${allname}, ${age} years old`;
   console.log(writer);
   // 这种思想在python或R中都有所体现，但请注意各自的语法
   ```

   所以一个很好的习惯就是用**反引号**代替双引号或单引号，模板字符串的另一个好处是多行字符串换行时，不需要使用 `\n\`符号：

   ```js
   console.log(`string with
   multiple
   lines`);
   ```

6. JavaScript 控制结构

   1. if else 判断

   ```js
   const age = 20;
   if(age >= 18) {
       console.log(`You are an adult 😃`);
   } else if{
       console.log(`You still have ${18-age} years left to be an adult`);
   } else{
       console.log(`emm...`);
   }
   // win + ; 可以打出表情！！
   ```

## JavaScript 书写位置

1. 内联其位于头部元素中， 且被 `<script></script>`元素封装。
2. fdaf

   ```html
   <body>
     <script src="script.js"></script>
   </body>
   ```
