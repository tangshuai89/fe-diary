# Charater 2

## 第二天

### html html的元素有哪些（包括h5）

#### 第一次回答

> head: meta/link/script

> body: 

    block: 
        - h1-h6
        - ul-li
        - dl-dt
        - ol-li
        - div
        - header
        - footer
        - section
        - aside
        - p
        - input
        - textarea
        - button
        - img
        - canvas
        - video 
        - music
        - svg及相关
        - article
        - blockquote
        - quote
        - code
    inline-block:
        - a
        - span
        - i
        - em
    table-cell:
        - table
        - tr
        - td
        - th
        
#### 参考答案

行内元素：
a
b
span
strong
i
em
button
input
label
br
textarea
select
块元素
div
p
h1-h6
ol
ul
li
table
tbody
td
tr
thead
dl
dt
dd
H5新增元素
section
article
audio
video
hearder
footer
small


### css CSS3有哪些新特性

#### 第一次回答

布局相关
- 增加了流式布局相关（display: flex, flex: number, justify-content, align-items, flex-wrap, flex-direction）
- 盒模型更新，box-sizing增加了content-box与（记不住了） 一个算padding一个不算
- 增加了em与rem，用于精确计算级联尺寸，em继承父级，rem继承根
- border增加了border-radius用于绘制弧形
- 增加了伪类 ::before ::after
- background增加了background-size, background-clip
- line-gradient渐变
- media-query
- animation
- keyframe
- 颜色翻转（属性名称忘了）
- xs xm
- text-intelligence
- rgba

#### 参考答案

边框(borders):
border-radius 圆角
box-shadow 盒阴影
border-image 边框图像
背景:
background-size 背景图片的尺寸
background_origin 背景图片的定位区域
background-clip 背景图片的绘制区域
渐变：
linear-gradient 线性渐变
radial-gradient 径向渐变
文本效果;
word-break
word-wrap
text-overflow
text-shadow
text-wrap
text-outline
text-justify
转换：
2D转换属性
transform
transform-origin
2D转换方法
translate(x,y)
translateX(n)
translateY(n)
rotate(angle)
scale(n)
scaleX(n)
scaleY(n)
rotate(angle)
matrix(n,n,n,n,n,n)
3D转换：
*3D转换属性：

transform
transform-origin
transform-style
3D转换方法
translate3d(x,y,z)
translateX(x)
translateY(y)
translateZ(z)
scale3d(x,y,z)
scaleX(x)
scaleY(y)
scaleZ(z)
rotate3d(x,y,z,angle)
rotateX(x)
rotateY(y)
rotateZ(z)
perspective(n)
过渡
transition
动画
@Keyframes规则
animation
弹性盒子(flexbox)
多媒体查询@media


### js 写一个方法去掉字符串中的空格

#### 第一次作答

```javascript
  function trim(str) {
    return str.split(" ").join('');
  }
  trim("a x b x x c");

  function trim(str) {
    var newstr = '';
    for (var i = 0; i < str.length; i++) {
      if (str.charCodeAt(i) !== 32) {
        newstr += str.charAt(i);
      }
    }
    return newstr;
  }
  trim("a x b x x c");
```

#### 参考答案

``` javascript
String.prototype.myTrim = function(option){
  var _this = this;
  var fn = {
    front:function(){
      return _this.replace(/^\s+/,'')
//       return _this.trimLeft()//或_this.trimStart() ie不支持
    },
    end:function(){
      return _this.replace(/\s+$/,'')
//       return _this.trimRight()//或 _this.trimEnd() ie不支持
    },
    frontEnd:function(){
      return _this.replace(/^\s+|\s+$/g,'');
//       return _this.trim()//--包括所有的空格字符 (space, tab, no-break space 等)以及所有的行结束符（如 LF，CR）
//       return _this.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');
/* 某些软件，在保存一个以UTF-8编码的文件时，会在文件开始的地方插入三个不可见的字符（0xEF 0xBB 0xBF，即BOM），
转码后是“\uFEFF”，因此我们在读取时需要自己去掉这些字符。
“\xA0”其实就是HTML中常见的“&nbsp;” */
    },
    content:function(){
      var mStr = this.all();
      var lStr = _this.match(/^\s+/)[0];
      var rStr = _this.match(/\s+$/)[0]
      return lStr + mStr + rStr
    },
    all:function(){
      return _this.replace(/\s+/g,'')
    }
  }
  return fn[option]();
}
var str = '  s t  r  ';
var _str = {}
_str.front = str.myTrim('front')
_str.end = str.myTrim('end')
_str.frontEnd = str.myTrim('frontEnd')
_str.content = str.myTrim('content')
_str.all = str.myTrim('all')
console.log(_str)

```


## 第二次作答

### html html的元素有哪些 包含h5

```html
block:
- h1-h6
- div
- p
- code
- blockquote
- header
- footer
- aside
- section
- article
- video
- audio
- canvas
- svg及相关
- img
- input
- form
- button
- pre
- ol li
- ul li
- dl dt

inline-block:
- i
- a
- span
- strong
- em
- del
- center

table-ceil:
- table
- th tr td
```

### css CSS3有哪些新增的特性

```css
box:
- border-radius
- border-image
- box-shadow
- box-sizing

flex:
- display: flex
- flex: number;
- flex-wrap
- flex-direction
- justify-content
- align-items

animate:
- trasnform
- transform3d
- animation
- keyframe
- background: linear-gradient

calculate:
- rgba
- calc
- em
- rem
- vm vh

performance:
- will-change
- text-emphasis
- viewport

```

### js 写一个方法去掉字符串中的空格

```javascript
function testTrim(str) {
  return str.split(" ").join();
}

function testTrim(str) {
  var newstr = ';'
  for (let i = 0; i < str.length; i++) {
    if (str.charCodeAt(i) !== 32) {
      newstr += str[i];
    }
  }
  return newstr;
}


```