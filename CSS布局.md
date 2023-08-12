# 								CSS布局

## 1.副标题

当一个标题内含有副标题时，可以在该标题内嵌套添加<small>元素或者给小标题元素应用样式类.small，这样可以得到一个字号更小、颜色更浅的文本，即副标题。通常与.text-muted类一起使用，将副标题的颜色变浅。

```html
<div class="container">
        <div class="row">
            <div class="col">
                <h1>一级标题h1.<small>我是h1的副标题</small></h1>
                <h1>一级标题h1.<small c1ass="text-muted">我是h1的副标题</sma11>
                </h1>
            </div>
        </div>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919411092.png)

## 2.排版内联文本

当一个标题内含有副标题时，可以在该标题内嵌套添加<small>元素或者给小标题元素应用样式类.small，这样可以得到一个字号更小、颜色更浅的文本，即副标题。通常与.text-muted类一起使用，将副标题的颜色变浅。

```html
<div class="col">
        <p>可以使用mark标识<mark>高亮</mark>文本。</p>
        <p><de1>这行使用del删除文本.</del></p>
        <p><s>这行文本使用的是s标签.</s></p>
        <p>这里使用ins标签插入文本：<ins>ins也是下划线的效果</ins>。</p>
        <p><u>使用u标签添加下划线</u></p>
        <p>这里用了small标签：<small>小号文字</small></p>
        <p>这行使用strong加粗文本：<strong>加粗效果</strong>。</p>
        <p>这行使用em标签，让文本变为斜体：<em>斜体效果</em>。</p>
        </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919512146.png)

## 3.排版文字颜色

Bootstrap 给文本提供了一组样式类，可以让文本展现不同的情景色，从而表达不同的意图。这些样式类也可以应用于链接，并会像我们的默认链接样式一样在悬停时变暗。

```html
<div class="col">
        <p class="text-muted">柔和文本：浅灰色</p>
        <p class="text-primary'">主要文本：蓝色</p>
        <p class="text-success">成功文本：绿色</p>
        <p class="text-info">信息文本：浅蓝色</p>
        <p class="text-warning'">警告文本：黄色</p>
        <p class="text-danger">危险文本：褐色</p>
        <!-- <a href="#" class=:"text-danger">危险文本：褐色</a> -->
    </div>
    <div class="col">
        <p class="text-secondary">副标题文本：灰色</p>
        <p class:="text-dark">深色文本：深色</p>
        <p class="text-body">body文本：深色</p>
        <p class="text-light bg-dark">浅色文本：浅色</p>
        <p class="text-white bg-dark">白色文本：白色</p>
        <p class="text-black">黑色文本：黑色</p>
        </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919600727.png)

## 4.文本排列对齐效果

Bootstrap提供了.text-left、.text-right、.text-center、.text-justify、.text-X-*(其中X为屏幕宽度前缀sm、md、lg、xl，*为left、right、center、justify) 。 

```html
<div class="col">
        <p class="text-left">左对齐</p>
        <p class="text-center">居中</p>
        <p class="text-right">右对齐</p>
        <p class="text-justify">两端对齐效果：Hel1oHel1oHel1oHel1oHel1oHel1oHel1oHel1o</p>
        <p class="text-left">左边对齐效果：He11 o Hel1oHel1oHel1oHel1oHel1oHel1oHel1oHel1o</p>
        <p class="text-sm-right">在小屏下右对齐.</p>
        <p class="text-md-right">在中屏下右对齐，</p>
        <p class="text-lg-right">在大屏下右对齐.</p>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919681326.png)

## 5.预定义按钮

 Bootstrap为按钮提供了一个基本样式类.btn，所有按钮元素都使用它。此外，还提供了一些预定义样式类.btn-*，可以用来定义不同风格的按钮，其中*的取值：primary、secondary、success、danger、warning、info、light、dark、link。

```html
<button type="button" class="btn">基本按钮</button>
    <button type="button" class="btn btn-primary">主要按钮</button>
    <button type="button" class="btn btn-secondary">次要按钮</button>
    <button type="button" class="btn btn-success">成功</button>
    <button type="button" class="btn btn-info">信息</button>
    <button type="button" class="btn btn-warning">警告</button>
    <button type="button" class="btn btn-danger">危险</button>
    <button type="button" class="btn btn-dark">黑色</button>
    <button type="button" class="btn btn-light">浅色</button>
    <button type="button" class="btn btn-link">链接</button>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919778206.png)

## 6.按钮边框

.如果需要一个按钮，但不需要很深的背景颜色，则可以使用.btn-outline-*类来代替btn-*，其中*的取值为：primary、secondary、success、danger、warning、info、light、dark。btn-outline-*类中定义了按钮的边框、浅色背景、按钮文字的颜色、鼠标滑过的效果、获得焦点的效果等。

```html
 <button type="button" class="btn btn-outline-primary">主要按钮</button>
    <button type="button" class="btn btn-outline-secondary">次要按钮</button>
    <button type="button" class="btn btn-outline-success">成功</button>
    <button type="button" class="btn btn-outline-info">信息</button>
    <button type="button" class="btn btn-outline-danger">警告</button>
    <button type="button" class="btn btn-outline-warning">危险</button>
    <button type="button" class="btn btn-outline-light ">浅色</button>
    <button type="button" class="btn btn-outline-dark">黑色</button>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919849165.png)

## 7.块级按钮

给按钮<button>元素应用样式类.btn-block可以将按钮拉伸至其父元素100%的宽度，同时该按钮变为了块级元素。

```html
<div style="width: 200px;">
        <button type="button" class="btn btn-primary btn-block">块级按钮</button>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679919923151.png)

## 8.缩略图组件

缩略图用于给图片、视频、文本等加入栅格功能，很适合以网格形式展示图片、视频、商品列表等。默认的缩略图非常简单，只需把图片放在 **class=“thumbnail”** 的 a 标签中即可。

```html
<div class="container">
        <div class="row">
            <div class="col">
                <div class="thumbnail">
                    <img src="./img/1.png" alt="" class="img-thumbnail">
                    <div class="caption">
                        <h3>小五教你做前端</h3>
                        <p>知名博主为你提供优质视频</p>
                        <button type="button" class="btn btn-primary">添加购买</button>
                        <button type="button" class="btn btn-light">课程预览</button>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="thumbnail">
                    <img src="./img/2.gif" alt="" class="img-thumbnail">
                    <div class="caption">
                        <h3>高耸入云，薄雾萦绕</h3>
                        <p>带你看最好看的风景</p>
                        <button type="button" class="btn btn-primary">添加购买</button>
                        <button type="button" class="btn btn-light">课程预览</button>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="thumbnail">
                    <img src="./img/3.gif" alt="" class="img-thumbnail">
                    <div class="caption">
                        <h3>风景描述，总结概括</h3>
                        <p>总结概括，日出风景</p>
                        <button type="button" class="btn btn-primary">添加购买</button>
                        <button type="button" class="btn btn-light">课程预览</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679920002845.png)

## 9.文本变换大小写

.text-lowercase：将大写字母转换为小写字母。

.text-uppercase：将小写字母转换为大写字母。

.text-capitalize：将文本首字母转换为大写。 

```html
<div class="col">
        <p class="text-lowercase">将大写转换为小写"ABC</p>
        <p class="text-uppercase">将小写转换为大写:abc</p>
        <p class="text-capitalize">将首字母转换为大写:alice</p>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679920089037.png)

## 10.内联列表

.给列表<ul>或<ol>元素应用样式类.list-inline，对<li>应用样式.list-inline-item

```html
<div class="col">
        <h6>内联列表/横向放置的列表</h6>
        <ul class="list-inline">
            <li class="list-inline-item">HTML</li>
            <li class="list-inline-item">CSS</li>
            <li class="list-inline-item">JavaScript</li>
            </u1>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679920220010.png)

## 11.水平描述列表

使用栅格系统水平排列，使用.text-truncate来截断文字。

```html
<div class="container">
        <dl class="row">
            <dt class="col-3">HTML</dt>
            <dd class="col-9">超文本标记语言，标准通用标记语言下的一个应用。HTML不是一种编程语言，而是一种标记语言(markup
                language),是网页制作所必备的。</dd>
            <dt class="col-3">CSS</dt>
            <dd class="col-9">层叠样式表是一种用来表现HTML或XML等文件样式的计算机语言。CSS不仅可以静态地修饰网页，
                还可以配合各种脚本语言动态地对网页各元素进行格式化。</dd>
            <dt class="col-3 text-truncate">JavaScript脚本语言语言语言语言语言语言语言语言语言语言语言</dt>
            <dd class="col-9">JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型</dd>
        </dl>
    </div>
```

![](https://cdn.jsdelivr.net/gh/TroyTrojan/PictureBed/1679920280563.png)