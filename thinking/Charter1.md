# Charater 1

- 来源于 https://github.com/haizlin/fe-interview/blob/master/category/history.md

## 第一天

### html 页面导入样式时，使用link与@import的区别

#### 第一次回答：
- link可以引入外部资源，@import不行
- link是HTML标签，@import不是

#### 参考答案：
  - link是XHTML标签，除了加载CSS外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CS- link引用CSS时候页面载入时同时加载，@import需要页面网页完全载入以后加载
  - link是XHTML标签，无兼容问题；@import是CSS2.1提出的，低版本的浏览器（IE5以下）不支持
  - link支持使用javascript控制DOM进行改变样式，@import不支持
  - 必须在<style></style>标签内使用
   
### css 圣杯布局和双飞翼布局的理解和区别，并用代码实现

### 第一次回答

- 圣杯布局为长条header与footer，左右侧固定aside，中间固定content
- 双飞翼布局也是长条header与footer，左右侧固定aside，中间固定content
- 圣杯布局是负边距布局，双飞翼是float布局


> 圣杯
```html

<div class="container">
    <div class="left"></div>
    <div class="content"></div>
    <div class="right"></div>
</div>

<style type="text/css">
    .container {
        width: 100%;
        height: 400px;
    }
    .left {
        width: 200px;
        height: 400px;
        float: left;
    }
    .right {
        width: 200px;
        height: 400px;
        float: right;
    }
    .content {
        width: 100%
        padding: 0 200px;
    }
</style>

```

> 双飞翼
```html

<div class="container">
    <div class="left"></div>
    <div class="content"></div>
    <div class="right"></div>
</div>

<style type="text/css">
    .container {
        width: 100%;
        height: 400px;
    }
    .left {
        width: 200px;
        height: 400px;
        float: left;
        background: #ff0000;
    }
    .right {
        width: 200px;
        height: 400px;
        float: left;
        background: #ff0ff0;
    }
    .content {
        width: 100%;
        float: left;
    }
</style>

```


### 参考答案

> 作用：圣杯布局和双飞翼布局解决的问题是一样的，就是两边顶宽，中间自适应的三栏布局，中间栏要在放在文档流前面以优先渲染。
> 区别：圣杯布局，为了中间div内容不被遮挡，将中间div设置了左右padding-left和padding-right后，将左右两个div用相对布局position: relative并分别配合right和left属性，以便左右两栏div移动后不遮挡中间div。双飞翼布局，为了中间div内容不被遮挡，直接在中间div内部创建子div用于放置内容，在该子div里用margin-left和margin-right为左右两栏div留出位置。

```html

<body>
<div id="hd">header</div>
<div id="bd">
  <div id="middle">middle</div>
  <div id="left">left</div>
  <div id="right">right</div>
</div>
<div id="footer">footer</div>
</body>

<style>
#hd{
    height:50px;
    background: #666;
    text-align: center;
}
#bd{
    /*左右栏通过添加负的margin放到正确的位置了，此段代码是为了摆正中间栏的位置*/
    padding:0 200px 0 180px;
    height:100px;
}
#middle{
    float:left;
    width:100%;/*左栏上去到第一行*/
    height:100px;
    background:blue;
}
#left{
    float:left;
    width:180px;
    height:100px;
    margin-left:-100%;
    background:#0c9;
    /*中间栏的位置摆正之后，左栏的位置也相应右移，通过相对定位的left恢复到正确位置*/
    position:relative;
    left:-180px;
}
#right{
    float:left;
    width:200px;
    height:100px;
    margin-left:-200px;
    background:#0c9;
    /*中间栏的位置摆正之后，右栏的位置也相应左移，通过相对定位的right恢复到正确位置*/
    position:relative;
    right:-200px;
}
#footer{
    height:50px;
    background: #666;
    text-align: center;
}
</style>

```

> 双飞翼

```html

<body>
<div id="hd">header</div> 
  <div id="middle">
    <div id="inside">middle</div>
  </div>
  <div id="left">left</div>
  <div id="right">right</div>
  <div id="footer">footer</div>
</body>

<style>
#hd{
    height:50px;
    background: #666;
    text-align: center;
}
#middle{
    float:left;
    width:100%;/*左栏上去到第一行*/     
    height:100px;
    background:blue;
}
#left{
    float:left;
    width:180px;
    height:100px;
    margin-left:-100%;
    background:#0c9;
}
#right{
    float:left;
    width:200px;
    height:100px;
    margin-left:-200px;
    background:#0c9;
}

/*给内部div添加margin，把内容放到中间栏，其实整个背景还是100%*/ 
#inside{
    margin:0 200px 0 180px;
    height:100px;
}
#footer{  
   clear:both; /*记得清楚浮动*/  
   height:50px;     
   background: #666;    
   text-align: center; 
} 
</style>

```

### js 用递归算法实现，数组长度为5且元素的随机数在2-32间不重复的值

#### 第一次回答

``` javascript

function generateArray(arr) {
    var item = Math.round(2 + Math.random() * 30);
    arr.push(item);
    if (arr.length < 5) {
        return generateArray(arr);
    }
    return arr;
}

var arr = [];
generateArray(arr);

```

#### 参考答案

> 第一次回答主要错误在可能会有重复，增加一个if判定如果重复直接递归一次
> 参照较为严谨的回答，随机这个实现可能是有问题的，但觉得第一次回答的实现较为正常，不玩技巧

``` javascript

// 6 行写完
function buildArray(arr, length, min, max) {
    var num = Math.floor(Math.random() * (max - min + 1)) + min;
    if (!arr.includes(num)) { arr.push(num); }
    return arr.length === length ? arr : buildArray(arr, length, min, max);
}
var result = buildArray([], 5, 2, 32);
console.table(result);

```