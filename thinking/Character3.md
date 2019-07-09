## 第一次作答

### html html全局属性(global attribute)有哪些（包含h5)?

- tag
- name
- class
- id
- data-

### css 在页面中隐藏元素的方法有哪些？

- visible: hidden;
- display: none;
- position: absolute; top left 为负值
- z-index设置较低，其他元素父级设置较高
- opacity: 0
- overflow； hidden: height=0
- ::before ::after

### js 去除字符串中最后一个指定的字符

```javascript
function actionDeleteLastSpecifiedChar(string_origin, string_del) {
  var position = 0;
  var charcode_string_del = string_del.charCodeAt(0);
  for (var i = 0; i < string_origin.length; i++) {
    if (string_origin.charCodeAt(i) === charcode_string_del) {
      position = i;
    }
  }
  return position;
}

```

## 参考答案

### html全局属性

https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes

- accesskey
- autocapitalize
- class
- contenteditable
- contextmenu
- data-*
- dir
- draggable
- dropzone
- exportparts
- hidden
- id
- inputmode
- is
- itemid
- itemprop
- itemref
- itemscope
- itemtype
- lang
- part
- slot
- spellcheck
- style
- tabindex
- title
- translate

### css 

- display: none
- opacity: 0
- visibility: hidden
- z-index: -9999999999999
- transform: scale(0)
- margin-left: -100%
- position: relative; left: -100%
- width: 0; height: 0;

### js

```javascript
function delLast (str,del) {
    if (tpeof str !== 'string') {
      alert('请确认要删除的对象为字符串！');
      retrun false;
    } else {
      let index = str.lastIndexOf(del);
      str.substring(0,index ) + str.substring(index+1,str.length);
    }
}

```