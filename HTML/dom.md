# DOM
文档对象模型。

## dom树

1. 隐藏元素的方式

+ 占位隐藏
  + opacity: 0
  + visibility: hidden

+ 不占位隐藏
  + display: none
  + 绝对定位后移出视野

## dom事件

### dom0级事件

绑定方式，以click事件为例子：
```
dom元素.onclick = function() {};
```
使用该方式需要注意：
1. 只能绑定一个事件，后面绑定的事件会覆盖掉前面的事件。
2. 回调方法内使用this时，指向不一样。
3. 解绑的话，重新赋值就行了。
4. 事件之前需要写 'on'

### dom1级事件

#### W3C标准
使用addEventListener/removeEventListener方法，以click为demo：
```
dom元素.addEventListener('click', function() {}, 是否冒泡(true/false))
```

#### 低版本IE事件


## scroll***、offset*** 与 client***
### scroll***
+ scrollHeight：获取对象的滚动高度（实际内容的高度）
+ scrollWidth：获取对象的滚动宽度（实际内容的宽度）
+ scrollLeft：设置和获取对象已经滚动的宽度（偏移）。
+ scrollTop：设置和获取对象已经滚动的高度（偏移）。

### offset***
+ offsetHeight：获取当前对象的高度（不包括margin）。
+ offsetWidth：获取当前对象的宽度（不包括margin）。
+ offsetTop：获取当前对象相对与已定位的父元素的top值（该元素border到定位父元素的border的间距）。
+ offsetLeft：获取当前对象相对与已定位的父元素的left值（该元素border到定位父元素的border的间距）。
+ offsetParent：已定位的上层父级元素。如果无定位，则视为html根元素。

### client***
+ clientHeight：获取对象当前的高度（仅padding+内容）。
+ clientWidth：获取对象当前的宽度（仅padding+内容）。
+ clientLeft：获取当前对象的左边框（border）宽度。
+ clientTop：获取当前对象的上边框（border）宽度。

## attribute和property的区别

+ property 是 DOM 中的属性，是 js 里的对象。
+ attribute 是 HTML 标签上的特性，它的值只能够是字符串。

### attribute
简单理解，Attribute就是dom节点自带的属性，例如html中常用的id、class、title、align等。  
attributes是属于property的一个子集，它保存了HTML标签上定义属性。

#### 取值/赋值
getAttribute() 和 setAttribute()

### property
常用的Attribute，例如id、class、title等，已经被作为Property附加到DOM对象上，可以和Property一样取值和赋值。但是自定义的Attribute就不行了。

#### 取值/赋值
用"."就行，

？？？
property能够从attribute中得到同步；
attribute不会同步property上的值；
attribute和property之间的数据绑定是单向的，attribute->property；
更改property和attribute上的任意值，都会将更新反映到HTML页面中；

对于html的标准属性来说，attribute和property是同步的，是会自动更新的
但是对于自定义的属性来说，他们是不同步的

## 页面加载

+ Load 事件触发代表页面中的 DOM，CSS，JS，图片已经全部加载完毕。
+ DOMContentLoaded 事件触发代表初始的 HTML 被完全加载和解析，不需要等待 CSS，JS，图片加载。





































































