



# 1.1 为什么要学jQuery？

### 1.1.1 学习JS的遇到的痛点

痛点的总结：

1，多次书写window.onload事件会出现覆盖现象

2，代码容错性超级差

3，兼容性需要处理

4，实现简单功能，代码很繁琐

## 1.2jQuery是什么？

### 1.2.1 jQuery描述（理解）

jQuery是js的一个库，封装了我们开发过程中常用的一些功能，方便我们来调用，提高了我们的开发效率。

Js库是把我们常用的功能放到一个单独的文件中，我们用的时候，直接引用到页面里面来就可以了。

comment.js是我们自己封装的库，而jQuery是别人帮我们封装好的库。

### 1.2.2 学习jQuery，主要是学什么呢？

目前这个阶段，主要学习如何来使用jQuery操作DOM，其实就是学习jQuery封装好的那些功能方法，这些方法叫做API（Application Programming Interface应用程序编程接口）。

这些API的共同特点是：**几乎全都是方法**。所以，在使用jQuery的API时，都是方法调用，也就是说要加小括号()，小括号里面是相应的参数，参数不同，功能不同。

## 1.3 **如何使用jQuery？（**重点）

使用步骤： 

1．引包

2．入口函数

3．功能实现代码（事件处理）

 

## 1.4jQuery详细解释

### 1.4.1 版本介绍（了解） 

同版本两个文件的区别：

min：压缩版，压缩过后，体积会更小

压缩指的是：把注释、空格、换行全部去掉，把变量名称尽可能的换成更加简短的字符。

压缩的主要目的：就是让文件变的更小。

平时开发过程中，这两个文件使用哪个都可以；但是，项目上线的时候，推荐使用压缩版。

 

### 1.4.2 引包注意点（理解）

第一点：在使用jQuery之前，先把jQuery文件引到页面中来

​	如果在使用jQuery之前，没有引用jQuery文件，会报错：



第二点：src路径一定要写正确

​	如果src路径写错，也会报错：

 

### 1.4.3 jQuery的入口函数（重点）

第一种：$(window).load(function(){});

第二种：$(document).ready(function(){});

第三种：$(function(){});

以上三种写法：

第一种：

页面中所有的内容加载完毕后才触发

第二、三种：

页面中的基本的标签加载完毕后就可以触发了

 ~~~js
window.onload =  function(){JS操作}和$(function(){})（jQ操作）

书写方式不同 ：原生的页面加载事件（入口函数）用等号赋值，后面的入口函数会覆盖前面的
jq的入口函数 是通过方法调用 在$（）中传入一个匿名函数，后面的入口函数不会覆盖前面的

$(function(){})比window.onload更快，前者是DOM结构加载完成就执行  后者是页面上所有资源全部加载完毕后执行

 ~~~

### 1.4.4 jQuery的顶级对象（重点）

jQuery里面的$函数，根据传入参数的不同，进行不同的调用，实现不同的功能。返回的是jQuery对象

 顶级对象：jQuery===$

### 1.4.5jQuery对象和DOM对象的相互转换（难点）

$("#btn")本质上存储的就是DOM对象，所以可以使用[]的形式，来获取数组里面的元素

**DOM对象此处指的是：使用js操作DOM返回的结果。**

var btn = document.getElementById(“btnShow”); // btn就是一个DOM对象

**jQuery对象此处指的是：使用jQuery提供的操作DOM的方法返回的结果。**

jQuery拿到DOM对象后又对其做了封装，让其具有了jQuery方法的jQuery对象，说白了，就是把DOM对象重新包装了一下。

- DOM对象转换成jQuery对象：$(DOM对象) 

- jQuery对象转换成DOM对象：$(DOM对象) [0];

  ​						    $(DOM对象) .get(0)

所有这些，都体现了jQuery对js的封装！

 **字符串转jq对象不能有空格、回车字符**,字符串拼接时的回车符需要转义

## 1.5 为什么要使用jQuery选择器

### 1.5.1 JS提供的选择DOM元素的方法

考虑兼容性的话，js里面提供的选择DOM的方法只有两个：

| **JavaScript选择元素的方法：**                |                                    |
| ------------------------------------- | ---------------------------------- |
| **document.getElementById();**        | 通过id属性获取指定元素返回唯一的DOM对象             |
| **document.getElementsByTagName();**  | 通过标签名获取指定元素返回DOM**对象数组**（即使只有一个元素） |
| **document.getElementsByName**();     | 根据name属性的值获取元素返回DOM对象数组（即使只有一个元素）  |
| **document.getElementsByClassName()** | 根据的是类样式的名字来获取元素返回DOM对象数组（即使只有一个元素） |

正是因为js提供的选择DOM的方法太少了，满足不了我们平时开发的需要，所以，我们可以使用jQuery选择器来弥补这方面的不足。

### 1.5.2 什么是jQuery选择器

jQuery选择器是jQuery强大的体现，它提供了一组方法，让我们更加方便的获取到页面中的元素。（联想：CSS选择符）

 

## 1.6 强大的jQuery选择器（重点）

强大的原因：jQuery实现了从CSS1到CSS3所有的选择器以及其他常用的选择器。

各种选择器之间可以相互代替，所以，平时真正用到的只是最常用的选择器。

### 1.6.1基本选择器

| 符号(名称)  | 说明     |                                          |
| ------- | ------ | ---------------------------------------- |
| #       | Id选择器  | $(“#btnShow”).css(“color”, “red”);选择id为btnShow的**一个**元素（返回值为jQuery对象，下同） |
| .       | 类选择器   | $(“.liItem”).css(“color”, “red”);选择含有类liItem的**所有**元素 |
| element | 标签选择器  | $(“li”).css(“color”, “red”);选择标签名为li的所有元素 |
| 多条件选择器  | 并集选择器  | $("span,p,li,div").css("backgroundColor","yellow"); |
| 标签+类选择器 | 交集选择器  | $("li.cls").css("backgroundColor","yellow"); |
| 全选择器    | $('*') |                                          |

### 1.6.2层级选择器

| 符号(名称)           | 说明                                       |                                          |
| ---------------- | ---------------------------------------- | ---------------------------------------- |
| 空格               | 后代选择器    .find()                         | $(“#j_wrap li”).css(“color”, “red”);选择id为j_wrap的元素的所有后代元素li |
| >                | 子代选择器     .children()                    | $(“#j_wrap > ul > li”).css(“color”, “red”);选择id为j_wrap的元素的所有子元素ul的所有子元素li |
| one+two 相邻兄弟选择器  | 选取所有one元素同辈的下一个元素two（如果有几个one，就有几个two，除非紧挨着one后面没有同级元素two） | $("#dv+p").css("backgroundColor","red"); |
| one~two  一般兄弟选择器 | 选取one元素同辈的two的所有元素                       | $("#dv~p").css("backgroundColor","red")  |

### 1.6.3基本过滤选择器

| 符号(名称)         | 说明                         |
| -------------- | -------------------------- |
| :first         | 选取第一个元素（只匹配一个单独的元素）        |
| :last          | 选取最后一个元素                   |
| :not(selector) | 选取不是这个元素的其他元素              |
| :eq(index)     | 选择索引号为index的一个元素，index从0开始 |
| :odd           | 选择索引号为奇数的所有元素，index从0开始    |
| :even          | 选择索引号为偶数的所有元素，index从0开始    |
| :gt(index)     | 选取索引大于index的元素             |
| :lt(index)     | 选取索引小于index的元素             |
| :header        | 选取所有的标题元素，如h1,h2,h3        |
| :animated      | 选取当前正在执行动画的所有元素            |
| :focus         | 选取当前获取焦点的元素                |

### 1.6.4筛选选择器（方法）

| 符号(名称)                                   | 说明                                      |
| ---------------------------------------- | --------------------------------------- |
| .find(selector)                          | 查找指定元素的所有后代元素（子子孙孙）,参数必填                |
| .children()                              | 查找指定元素的直接子元素（亲儿子元素），参数可不填               |
| .siblings()                              | 查找所有兄弟元素（不包括自己）                         |
| .parent()                                | 查找直接的父级元素                               |
| :nth--(last)child(index/even/odd/equation) | 选取父元素下的第index个子元素或者奇偶元素，index从1算起       |
| :first-child                             | 获取（多）个父元素的第一个子元素                        |
| :last-child                              | 选取父元素的最后一个子元素                           |
| :eq(index)                               | 查找指定元素的第index个元素，index是索引号，从0开始         |
| index()                                  | 获取指定元素的索引号（从0开始的）                       |
| prevAll()                                | 获取指定元素之前的所有兄弟元素                         |
| nextAll()                                | 获取指定元素之后的所有兄弟元素                         |
| **内容过滤选择器**                              |                                         |
| :contains(text)                          | 选取（子元素）含有文本内容为“text”的元素                 |
| :empty                                   | 选取不包含子元素或者文本的空元素                        |
| :has(selector)                           | 选取含有选择器所匹配的元素的元素                        |
| :parent                                  | 选取含有子元素或者文本的元素                          |
| **可见性过滤选择器**                             |                                         |
| :hidden                                  | 选取所有不可见的元素                              |
| :visible                                 | 选取所有可见的元素                               |
| **属性过滤选择器**                              |                                         |
| [ attribute ]                            | 选取拥有此属性的元素                              |
| [ attribute = value ]                    | 选取属性的值为value的元素                         |
| [ attribute != value ]                   | 选取属性的值不等于value的元素                       |
| [ attribute ^= value ]                   | 选取以属性的值value开始的元素                       |
| [ attribute $= value ]                   | 选取属性的值以value结束的元素                       |
| [ attribute *= value ]                   | 选取属性的值含有value的元素                        |
| [ attribute \|= value ]                  | 选取属性等于给定字符串或以该字符串为前缀（该字符串后跟一个连字符‘-’）的元素 |
| [ attribute ~= value ]                   | 选取属性的值含有value的元素                        |

```
隐藏元素的方式：
CSS  display = none
type = 'hidden' 的表单元素
宽高都显示设置为0
祖级元素隐藏
CSS visibility = hidden/0
CSS opacity = 0

元素可见：宽或高大于0
CSS visibility = hidden/0
CSS opacity = 0
```



  $('input[type=text]');获得input中type属性值为text的标签

 .find(":checkbox")  获得后代元素中属性值为checkbox的标签

检查某个元素是否存在的方法：if($("#tt").length > 0) {}

### 1.6.5表单元素选择器

| 表单元素选择器                               |                                  |
| ------------------------------------- | -------------------------------- |
| $(':input')                           | 选择所有input，textarea，select，button |
| $(':text/password/submit/image/file') |                                  |
|                                       |                                  |
| 属性筛选选择器                               |                                  |
| $(':enabled')                         | 选取可用的表单元素                        |
| $(':enabled')                         | 选取不可用的表单元素                       |
| $(':checked')                         | 选取被选中的input元素                    |
| $(':selected')                        | 选取被选中的option元素                   |



## 1.7 jQuery部分方法的使用

### 1.7.1 操作样式的方法：

- 设置样式属性操作：css()
  - 设置单个样式：$(selector).css(“样式属性名称”, “样式属性值”);

  - 设置多个样式：（也可以设置单个） （推荐）

    $(selector).css({“color”: “red”, “fontSize”: “30px”});

  - 获取样式属性操作：

    参数表示要获取的 样式属性名称

    $(selector).css(“font-size”);

    此时，会返回”font-size”样式属性对应的值。

  - .css(propertyName,callback)  传入回调函数，返回修改属性值

- 添加类样式 .addClass(Srting)

  ~~~
  注意：1.参数加引号，为字符串类型   2.所有类操作的方法类名都不带点   3.多个类样式的名字中间用空格隔开
  ~~~

  添加多个类样式：

  $("#dv").addClass("cls cls2");

  $('#dv').addClass('cls').addClass('cls2')  	

- 移除类样式  .removeClass(Srting || 空)

  参数：不填参数，移除的是当前元素的所有的类样式

- 切换类样式：toggleClass(className) 

  该元素有类则移除，没有指定类则添加。会保留原来的类名后新增，用逗号隔开

  ~~~js
  //根据父元素来设置class属性
  $('div.foo').toggleClass(function() {
    if ($(this).parent().is('.bar') {
      return 'happy';
    } else {
      return 'sad';
    }
  });
    //每点击三下加上一次 'highlight' 类
     var count = 0;
    $("p").click(function(){
        $(this).toggleClass("highlight", count++ % 3 == 0);
    });
  ~~~

  ​

- 判断指定元素是否包含类 className  ：hasClass(calssName) 

  $(selector).hasClass(“liItem”);

  返回值：布尔值

  ~~~
  1 操作的样式非常少，那么可以通过.css()这个 方法来操作
  2 操作的样式很多，那么要通过使用类的方式来操作
  3 如果考虑以后维护方便（把CSS从js中分离出来）的话，推荐使用类的方式来操作。类比CSS书写位置（把css从html中分离出来）

  ~~~

~~~
样式的优先级：内联样式>内部样式>外部样式
.addClass(),处理的是内部样式或外部样式中定义好的，通过增添类名的方式，附加到元素上
一般用大于静态的HTML结构
.css(),处理的是内联样式，直接通过元素的style属性，附加到元素上
一般用于动态添加的元素
~~~





### 1.7.2 操作元素内容的方法

- html()方法：相当于innerHTML

  作用：设置或获取匹配元素的HTML内容

  - 获取操作不带参数			$(selector).html();

  - 设置操作带参数，参数表示要设置的HTML内容                 $(selector).html(“我是内容”);

    注意：html格式的字符串会被设置为**标签**

    ​


- text() 方法:相当于innerText

  作用：设置或获取匹配元素的合并文本

  - 获取操作不带参数		$(selector).text();

  - 设置操作带参数，参数表示要设置的文本内容           $(selector).text(“我是内容”);

  - #### function(index, text)

    此函数返回一个字符串。接受两个参数，index为元素在集合中的索引位置，text为原先的text值。

注意：html格式的字符串也会被设置为**文本**

~~~js
//使用函数来返回设置所有匹配元素的文本内容。
$("p").text(function(n){
    return "这个 p 元素的 index 是：" + n;
    });
~~~



###  1.7.5 JQ对象的遍历的方法

- .next();获取的是当前元素的下一个兄弟元素

    $(this).next().css("backgroundColor","green");

- .nextAll();获取的是当前元素的后面的所有的兄弟元素

  $(this).nextAll().css("backgroundColor","green");

- .prev();获取的是当前元素的前一个兄弟元素

  $(this).prev().css("backgroundColor","green");

- .prevAll();获取的是当前元素的前面的所有的兄弟元素

  $(this).prevAll().css("backgroundColor","green")

- .siblings();获取的是当前元素的所有的兄弟元素(自己除外)

  $(this).siblings().css("backgroundColor","green");

- .parent()  匹配合集中所有元素的直接父级元素

- parents()   匹配合集中所有元素的祖辈元素，可添加类名进行筛选

- closest()

    ~~~
    parents()和closest()的区别：
    起始位置不同：.closest开始于当前元素 .parents开始于父元素
    遍历的目标不同：.closest要找到指定的目标，.parents遍历到文档根元素，closest向上查找，直到找到一个匹配的就停止查找，parents一直查找到根元素，并将匹配的元素加入集合
    结果不同：.closest返回的是包含零个或一个元素的jquery对象，parents返回的是包含零个或一个或多个元素的jquery对象
    ~~~

    ​




### 1.7.6元素的数据储存data

html5 dataset是新的HTML5标准，允许你在普通的元素标签里嵌入类似data-*的属性，来实现一些简单数据的存取。它的数量不受限制，并且也能由JavaScript动态修改，也支持CSS选择器进行样式设置。这使得data属性特别灵活，也非常强大。有了这样的属性我们能够更加有序直观的进行数据预设或存储。那么在不支持HTML5标准的浏览器中，我们如何实现数据存取?  jQuery就提供了一个.data()的方法来处理这个问题；常常用于我们存放临时的一些数据，因为它是直接跟DOM元素对象绑定在一起的

jQuery提供的存储接口

~~~
jQuery.data( element, key, value )   //静态接口,存数据
jQuery.data( element, key )  //静态接口,取数据   
.data( key, value ) //实例接口,存数据
.data( key ) //实例接口,存数据

~~~

删除接口

~~~
jQuery.removeData( element [, name ] )
.removeData( [name ] )
~~~



# 2.1jQuery动画

jQuery提供的一组网页中常见的动画效果，这些动画是标准的、有规律的效果；同时还提供给我们了自定义动画的功能。

### 2.1.1 显示隐藏（方法）动画

- show方法

  作用：让匹配的元素展示出来

  - 不带参数，作用等同于 css(“display”, ”block”)

    /* 注意：此时没有动画效果 */         $(selector).show();

  - 参数为数值类型，表示：执行动画时长

    /* 单位为：毫秒（ms），参数1000表示1秒钟 */		$(selector).show(1000);

  - 参数为字符串类型，是jQuery预设的值，共有三个，

    分别是：slow、normal、fast           $(selector).show(“slow”);

  - 参数一可以是数值类型或者字符串类型

    参数二表示：动画执行完后立即执行的回调函数 （匿名函数）

    $(selector).show(2000, function() {});

△hide方法使用方式和show相同

### 2.1.2 滑入滑出动画

- 滑入动画效果（联想：生活中的卷帘门）

  作用：让元素以下拉动画效果展示出来

  $(selector).slideDown(speed,callback);

 注意：省略参数或者传入不合法的字符串，那么则使用默认值：400毫秒

（同样适用于fadeIn/slideDown/slideUp）

- 滑出动画效果

  作用：让元素以上拉动画效果隐藏起来

  $(selector).slideUp(speed,callback);

- 滑入滑出切换动画效果

  $(selector).slideToggle(speed,callback);

**改变元素的display，height，padding-top，padding-bottom,margin-top，margin-bottom属性值**

### 2.1.3淡入淡出动画

- 淡入动画效果

  作用：让元素以淡淡的进入视线的方式展示出来

  $(selector).fadeIn(speed, callback);

-  淡出动画效果

  作用：让元素以渐渐消失的方式隐藏起来

  $(selector).fadeOut(1000);

- 淡入淡出切换动画效果

  作用：通过改变不透明度（opacity），切换匹配元素的显示或隐藏状态(display)

  $(selector).fadeToggle('fast',function(){});

- 改变不透明度到某个值

  与淡入淡出的区别：淡入淡出只能控制元素的不透明度从 完全不透明(1) 到完全透明(0)；而fadeTo可以指定元素不透明度的具体值。**并且时间参数是必需的！**

  作用：调节匹配元素的不透明度属性 

  参数：

  - 第一个参数表示：时长

  - 第二个参数表示：不透明度值，取值范围：0-1

    $(selector).fadeTo(1000, .5); //  1000毫秒，不透明度从1达到0.5

   第一个参数为0，此时作用相当于：.css(“opacity”, .5);===

  $(selector).fadeTo(0, .5); 



jQuery提供的动画使用方法总结：



有规律的体现：

jQuery提供的这几个动画效果控制的CSS属性包括：高度、宽度、不透明度。{height:400px; width:300px; opacity:.4;}

这三个CSS属性的共性是：属性值只有一个，并且这个值是数值（去掉单位后）。

 

### 2.1.3自定义动画

**注意：所有能够执行动画的属性必须只有一个数字类型的值，属性名用驼峰表示法表示。**

比如：要改变字体大小，要使用：fontSize（font-size），不要使用：font

 

动画支持的属性：

参数：$(selector).animate(**params,[speed],[easing],[fn]**)

**params**:一组包含作为动画属性和终值的样式属性和及其值的集合

**speed**:三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)

**easing**:要使用的擦除效果的名称(需要插件支持).默认jQuery提供"linear" 和 "swing".

**fn**:在动画完成时执行的函数，每个元素执行一次。

~~~
params:
1.如果是一个数值，样式属性就会从当前的值渐变到指定的值。
2.如果使用的是“hide”、“show”或“toggle”这样的字符串值，则会为该属性调用默认的动画形式。
3.可以使用 em 和 % 单位

~~~

#### 案例

~~~js
//让指定元素左右移动
$("#right").click(function(){
  $(".block").animate({left: '+50px'}, "slow");
});

$("#left").click(function(){
  $(".block").animate({left: '-50px'}, "slow");
});

~~~

~~~js
//在600毫秒内切换段落的高度和透明度
$("p").animate({
   height: 'toggle', opacity: 'toggle'
 }, "slow");
~~~

~~~js

// 在一个动画中同时应用三种类型的效果
$("#go").click(function(){
  $("#block").animate({ 
    width: "90%",
    height: "100%", 
    fontSize: "10em", 
    borderWidth: 10
  }, 1000 );
});
~~~



 

### 2.1.4停止动画

**常用方式：$(selector).stop();**

作用：停止当前正在执行的动画,如果队列中有等待执行的动画(并且clearQueue没有设为true)，他们将被马上执行

- 第一个参数表示是否清空所有的后续动画
- 第二个参数表示是否立即执行完当前正在执行的动画

$(selector).stop(clearQueue,jumpToEnd);

 ~~~
为什么要停止动画？
如果一个以上的动画方法在同一个元素上调用，那么对这个元素来说，后面的动画将被放到效果队列中。这样就形成了动画队列。（联想：排队进站）
动画队列里面的动画不会执行，直到第一个动画执行完成。

 ~~~



解释：

当调用stop()方法后，队列里面的下一个动画将会立即开始。但是，如果参数clearQueue被设置为true，那么队列面剩余的动画就被删除了，并且永远也不会执行。

如果参数jumpToEnd被设置为true，那么当前动画会停止，但是参与动画的每一个CSS属性将被立即设置为它们的目标值。比如：slideUp()方法，那么元素会立即隐藏掉。如果存在回调函数，那么回调函数也会立即执行。

注意：如果元素动画还没有执行完，此时调用sotp()方法，那么动画将会停止。并且动画没有执行完成，那么回调函数也不会被执行。

 



 

## 2.2 jQuery节点操作

### 2.2.1动态创建元素

~~~js
DOM中创建元素:
1.document.write("标签代码");缺陷:页面加载后创建元素,会重绘页面
2.innerHTML  
3.document.createElement("标签的名字")

~~~

**jQuery中创建元素的方式:**

1. $("标签的代码")     var spanNode = (“<span>我是一个span元素</span>”);

2. 对象.html("标签的代码");（推荐使用）

   作用：设置或获取所选元素的html内容（包括 HTML 标记）

   设置内容的时候，如果是html标记，会动态创建元素，此时作用跟js里面的 innerHTML属性相同

   - 动态创建元素

     $(selector).html(‘<span>传智播客</span>’);

   - 获取html内容,自动解析标签

     $(selector).html();

   - 参数可以为数组

~~~js
 $(function () {
   $("#btnCreate").click(function () {
     var arr=[];
     //遍历数组
     for(var i=0;i<datas.length;i++){
       var obj=datas[i];//数组中的每一个对象
       //创建行和列,加入到tbody中
       arr.push("<tr><td><a href="+obj.url+">"+obj.name+"</a></td>      <td>"+obj.type+"</td>      		</tr>");
     }
     $("#tbd").html(arr);
   });
});
~~~

**替代标签里已有的元素**



### 2.2.2 插入元素

**1. append()**（**重点**）

​	作用：在被选元素内部的最后一个子元素（或内容）后面插入内容

​		（页面中存在或者创建出来的元素都可以）（类似appendChild）

​	参数：1）htmlString        $(selector).append('<div></div>');

​		   2）jQuery对象       node.append($(selector));

~~~
1.如果是页面中存在的元素，那么调用append()后，会把这个元素从原先的位置移除，然后再插入到新的位置。
2.如果是给多个目标追加一个元素，那么append()方法的内部会复制多份这个元素，然后追加到多个目标里面去。（最好不要这么做）
~~~

2. **appendTo()**

   作用：同append()，区别是：把$(selector)追加到node中去

   $(selector).appendTo(node); 

3. **prepend()**

   作用：在所有匹配元素的第一个子元素前面追加内容或节点

   node.prepend($(selector));

4. **prependTo()**

5. **after()**

   作用：在所有匹配元素之后，作为兄弟元素插入内容或节点

   node.after($(selector)); 

6. **before()**

   作用：在所有匹配元素之前，作为兄弟元素插入内容或节点

   node.before($(selector));

   ~~~
   1.before与after都是用来对相对选中元素外部增加相邻的兄弟节点
   2.2个方法都是都可以接收HTML字符串，DOM 元素，元素数组，或者jQuery对象，用来插入到集合中每个匹配元素的前面或者后面
   3.2个方法都支持多个参数传递after(div1,div2,....)
   ~~~

   ~~~
   注意： 1.字符串转jq对象不能有空格、回车字符出现
   		2.JS中不支持换行符，在使用拼接字符串创建元素时，需要将换行符使用转义符（\）进行转义
   ~~~

7. **insertBefore()**     **insertAfter()**



### 2.2.3清空元素

- $(selector).empty();

   清空匹配的元素集合中所有的子节点。

- $(selector).html(“”);（推荐使用）

  作用：清空指定元素的所有子元素（光杆司令）

  没有参数

- $(selector).remove();

   将元素自身移除，同时也会移除元素内部的一切，包括绑定的事件及与该元素相关的jQuery数据。

   参数：删除特定样式的标签    $("p").remove(".hello");

- detach()

   从当前页面中移除该元素，但保留这个元素的内存模型对象。

   所有绑定的事件、附加的数据等都会保留下来。

替换元素

**.replaceWith( newContent )**：用提供的内容替换集合中所有匹配的元素并且返回被删除元素的集合

**.replaceAll( target ) ****：**用集合的匹配元素替换每个目标元素

### 2.2.4复制元素

$(selector).clone();

作用：克隆匹配的DOM元素并且选中这些克隆的副本，返回值为复制的新元素

参数：**Events[,deepEvents]**

1:元素数据（data）内对象和数组不会被复制，将继续被克隆元素和原始元素共享。深复制的所有数据，需要手动复制每一个

2:一个布尔值，指示是否对事件处理程序和克隆的元素的所有子元素的数据应该被复制。

### 2.2.5 JSON

JSON:javaScript  Object Notation（JS的对象表示法）轻量级文本数据交换格式

储存和交换文本信息的语法，类似于XML，但比XML更小，更快，更容易解析

语法：1. 数据在键值对中

​	    2.数据由逗号分隔

​	    3.大括号保存对象

​	     4.中括号保存数组

## 2.3操作form表单

### 2.3.1 属性操作

attr()参数：  

- name

  获取属性：attr(要获取的属性名称)-----可以获取自定义属性或元素的特有属性返回对应属性的值     $(selector).attr(“title”);

- Map（对象） 

  设置多个属性$("img").attr({ src: "test.jpg", alt: "Test Image" });

- key，value

  设置属性：attr(要设置的属性名称,该属性名称对应的值)

  $(selector).attr(“title”, “传智播客”);

- key,function(index, attr)

  1:属性名称。

  2:返回属性值的函数,第一个参数为当前元素的索引值，第二个参数为原先的属性值。

  ~~~js
  //把src属性的值设置为title属性的值。
  $("img").attr("title", function() { return this.src });	
  //禁用页面上的所有复选框。
  $("input[type='checkbox']").prop({
    disabled: true
  });
  //通过函数来设置所有页面上的复选框被选中。
  $("input[type='checkbox']").prop("checked", function( i, val ) {
    return !val;
  });	
  ~~~

  removeAttr


- .prop()     -----------checked、selected、disabled、checkbox     可以改变元素的样式

  作用：用来获取和设置值为false或true的属性，以及元素标签自带的属性；**但不能用来获取自定义属性**

  （弥补了attr（）无法获取值为布尔值的属性的缺点）**attr('checked') 返回undefined**

  prop方法通常用来影响DOM元素的动态状态，而不是改变的HTML属性。例如：input和button的disabled特性，以及checkbox的checked特性。

  参数同上

  ~~~js
  //选中复选框为true，没选中为false
  $("input[type='checkbox']").prop("checked");

  //禁用和选中所有页面上的复选框。
  $("input[type='checkbox']").prop("disabled", false);
  $("input[type='checkbox']").prop("checked", true);

  //通过函数来设置所有页面上的复选框被选中。
  $("input[type='checkbox']").prop("checked", function( i, val ) {
    return !val;
  });
  ~~~

  ​

- .removeAttr()  移除属性

   参数：要移除的属性的名称

     $(selector).removeAttr(“title”);  



~~~
属性和特性的区别：
特性（Attritube）：dom节点自带的属性（id,class,title），值可以为对象、数值、字符串等
属性（Property）：DOM元素作为对象所附加的内容，值只能为字符串或null，DOM对象中

只有非自定义的特性才会以属性形式添加到DOM对象中才可以用   Element.属性   获取
为DOM元素添加一个自定义属性，不会自动成为元素的特性

~~~

~~~
jquery中attr()、data()和prop()的区别：
attribute表示HTML文档节点属性，property表示JS对象的属性
从性能上对比，.prop() > .data() > .attr()
1.attr()用于设置或获取指定DOM元素所对应的文档节点上的属性(attribute)。
2.prop()用于设置或获取指定DOM元素(指的是JS对象，Element类型)上的属性(property);
3.attr()主要依赖的是Element对象的getAttribute()和setAttribute()两个方法。
4.prop()主要依赖的则是js中原生的对象属性获取和设置方式
5.大部分attribute与property是一一对应关系，DOM元素某些属性的更改也会影响到元素节点上对应的属性（id，class）
6.attr()设置的属性值只能是字符串类型，如果不是字符串类型，也会调用其toString()方法将其转换为字符串类型。获取的值为字符串或者null
7.prop()设置的属性值可以为包括数组和对象在内的任意类型。
8.对于a标签的href属性，prop()与attr()取得的值不同，prop是绝对地址，attr()取的就是href中的值

9.data()是从 Jquery的data对象 中取值，由于对象属性值保存在内存中，因此可能和视图里的属性值（attr所获取的）不一致的情况
~~~



### 2.3.2值和内容

val()方法：

- 作用：设置或返回表单元素value属性的值，例如：input,select,textarea的值

  获取匹配元素的值，只匹配第一个元素		$(selector).val();

  可以返回任意元素的值了。包括select。如果多选，将返回一个数组，其包含所选的值。

- 设置所有匹配到的元素的值                   $(selector).val(“具体值”);

~~~js
//val（）可以改变下拉框的选中值
 $('#btn').click(function(){$('select').val(3);})//option要设置对应的value值
~~~

获得文本域textarea中的内容：

1. ​    .text()方法  
2. ​    .val()方法--推荐

~~~
.text(),.html(),.val()差异：
1、.html()用来获取元素的html内容（包括标签）；.text()用来获取元素的纯文本内容，包括后代元素；
.val()用来读取表单的value值
2,、使用在多个元素上时，.html()、.val()值读取匹配到的第一个元素；.text()将会读取所选中元素的合并文本内容
3、当运用在多个元素上替换内时，会替换所有选中元素的内容
4、都可以使用回调函数的返回值，来动态地改变多个元素的内容
~~~



## 2.4 尺寸位置操作

### 2.4.1 高度和宽度操作

- 高度操作height() ： 

  作用：设置或获取匹配元素的height属性值

  - 带参数（数值类型||字符串类型）表示设置高度      $(selector).height(200);
  - 不带参数获取高度 （数值类型）        $(selector).height();

宽度操作width() ： 同上

~~~
css()获取高度和height获取高度的区别？
css()获取高度 返回值为String类型
height()获取高度   返回值为Number类型
~~~

 innerWidth（）获取当前元素的内容宽度+padding

outerWidth()获取当前元素的width+padding+border

outerWidth(true)获取元素的width+padding+border+margin

### 2.4.2 坐标值操作

- offset() 

  作用：获取或设置元素相对于浏览器左上角的位置

  - 无参数表示获取，返回值为：{left:num, top:num}，值是相对于document的位置

    $(selector).offset();  

    $(selector).offset().top

  - 有参数表示设置，参数推荐使用数值类型

    $(selector).offset({left:100, top: 150});

注意点：设置offset后，如果元素没有定位(默认值：static)，则被修改为relative

 

- scrollTop() 

  作用：获取或者设置元素垂直方向滚动的位置

  - 无参数表示获取滚动距离      $(selector).scrollTop();
  - 有参数表示设置偏移，参数为数值类型     $(selector).scrollTop(100);



- scrollLeft() 

  作用：获取或者设置元素水平方向滚动的位置

  $(selector).scrollLeft(100);



# 3.1jQuery事件机制

jQuery的事件机制，指的是：jQuery对JavaScript操作DOM事件的封装，包括了：事件绑定、事件解绑、事件触发。

~~~js
JavaScript：
btn.onclick = function() {}; // 表示：给这个按钮绑定事件
jQuery：
$btn.click(function() {});  // 表示：给按钮绑定事件（click是一个方法，内部是对onclick这个事件的封装）
~~~



### 3.2jQuery事件的发展历程（了解）

简单事件绑定 >> bind事件绑定 >> delegate事件绑定 >> on【重点】

 ~~~
l 简单事件绑定：
click(handler) 				单击事件
blur(handler) 				失去焦点事件
mouseenter(handler) 		鼠标进入事件
mouseleave(handler)			鼠标离开事件
dbclick(handler) 			双击事件
change(handler) 改变事件，如：文本框值改变，下来列表值改变等
focus(handler) 				获得焦点事件
keydown(handler) 			键盘按下事件
 ~~~



- bind()方式（不推荐，1.7以后的jQuery版本被on取代）

  作用：给匹配到的元素直接绑定事件

  参数：1）两个参数：绑定事件的名称（多个事件用空格隔开）字符串形式，事件处理函数

  ​		$("p").bind("click mouseenter", function(){});

  ​	    2）一个参数：对象{事件名1：事件处理函数，事件名2：事件处理函数，。}

  ~~~
  比简单事件绑定方式的优势：
  1.多个事件绑定同一个函数 比如：bind(“mouseenter  mouseleave”, function(){})
  2.多个事件绑定不同函数   bind({mouseover:function(){}, mouseout:function(){}});
  3.将数据传递到处理程序
  缺点：要绑定事件的元素必须存在文档中。
  ~~~

  ​


- 父级元素.delegate()方式（特点：性能高，支持动态创建的元素）

  作用：给匹配到的元素绑定事件，对支持动态创建的元素有效

  参数： 第一个参数：selector，要绑定事件的子元素

  ​	    第二个参数：事件类型

  ​	    第三个参数：事件处理函数

  $(".parentBox").delegate("p", "click", function(){})      为 .parentBox下面的所有的p标签绑定事件

与前两种方式最大的优势：减少事件绑定次数提高效率，**支持动态创建出来的元素绑定事件**！

~~~js
$("table").each(function(){    $("td", this).live("hover", function(){          $(this).toggleClass("hover");    });    
});

$("table").delegate("td", "hover", function(){    $(this).toggleClass("hover");
});
~~~



- 父级元素.on()方式

  （最现代的方式，兼容zepto(移动端类似jQuery的一个库)，强烈建议使用的方式）

  ​作用：给匹配的元素绑定事件，包括了上面所有绑定事件方式的优点

~~~js
两个参数:1事件的名字,2事件处理函数
 //$("#btn").on("click",function () {})              
三个参数: 1,事件的名字, 2.要绑定事件的元素--p,3事件处理函数
//$("#dv").on("click","p",function () {});
on是父级元素调用,目的:为子级元素去绑定事件
	
~~~

// 第一个参数：events，绑定事件的名称可以是由空格分隔的多个事件（标准事件或者自定义事件）

// 第二个参数：selector, 执行事件的后代元素

// 第三个参数：data，传递给处理函数的数据，事件触发的时候通过event.data来使用

// 第四个参数：handler，事件处理函数

可以给动态添加的元素，添加绑定事件，但不能直接给动态元素绑定 需要给动态添加的元素的 父级/祖级静态元素绑定事件 

### 3.3 事件解绑

- unbind() 方式

  作用：解绑 bind方式绑定的事件

  - $(selector).unbind(); //解绑所有的事件
  - $(selector).unbind(“click”); //解绑指定的事件

- undelegate() 方式

  作用：解绑delegate方式绑定的事件

  - $( selector ).undelegate(); //解绑所有的delegate事件
  - $( selector).undelegate( “click” ); //解绑所有的click事件
  - $("#dv").undelegate("p","click");//为div中p解除绑定事件


- **off解绑on方式绑定的事件（重点)**

  - 解绑匹配元素的所有事件

    $(selector).off();


  - 解绑匹配元素的所有click事件

    $(selector).off(“click”);


  - 解绑所有子元素的click事件，父元素的事件不会被解绑 

    $(selector).off( “click”, “**” ); 

​     //如果说父级元素和子级元素都是通过正常的方式绑定事件,如果通过off解绑的时候,父级元素的事件解绑了,子级元素的事件没有解绑

​      //但是:如果子级元素是通过父级元素调用delegate的方式绑定的事件,父级元素使用off方式解绑事件,这个时候父级元素和子级元素的相同的事件都会被解绑

### 3.4事件触发

- 简单事件触发

  $(selector).click(); //触发 click事件

- trigger方法触发事件（参数必填）

  $(selector).trigger(“click”);

- triggerHandler触发 事件响应方法（参数必填）

  $(selector).triggerHandler(“focus”);

  不触发浏览器默认行为（用在不触发submit上时）   比如:文本框获得焦点的默认行为

~~~
trigger返回调用者的jq对象；会触发事件冒泡
triggerHandler返回undefined；不会触发事件冒泡；不会触发默认事件
~~~

### 3.5jQuery事件对象介绍

event.delegateTarget			 调用绑定事件的元素

event.currentTarget 			真正绑定事件的元素

event.target					触发绑定事件的元素，等同于this

event.data 					传递给事件处理程序的额外数据	

event.type 					事件类型：click，dbclick

event.keyCode				键盘按键代码

event.pageX 					鼠标相对于页面左边的位置

**event.stopPropagation()；**	阻止事件冒泡（事件传播）

**event.preventDefault();** 		取消默认行为

return false; 					同时具有阻止冒泡和阻止默认行为的功能。

~~~js
绑定事件的参数-------event（形参）表示一个事件对象，当你触发事件，js会传一个参数给我，我们没有接受，参数依然存在arguments[0]；可以利用形参取接受：event

DOM的事件对象：MouseEvent
JQ的事件对象：jQuery.Event
jQuery.Event.originalEvent == MouseEvent

~~~



## 1.3 jQuery补充

### 1.3.1 链式编程

链式编程代码示例

$(“li”).parent(“ul”).parent(“div”).siblings(“div”).children(“div”).html(“内容”);

链式编程原理：return this;

通常情况下，只有设置操作才能把链式编程延续下去。因为获取操作的时候，会返回获取到的相应的值，无法返回 this。

 ~~~js
  function Student(name) {
            this.name=name;
            this.sayHi=function (name) {
                //判断sayhi()方法中，是否传入了参数
                if(name){
                    console.log("俺是"+name);
                    console.log(this)
                    return this;//把当前实例对象返回
                }else{
                    console.log("我的名字叫"+this.name);
                }
            };
            this.eat=function () {
                console.log("我就是喜欢吃大蒜+榴莲+臭豆腐");
            };
        }
        var stu=new Student("小明");
        stu.sayHi('小红').eat();
 ~~~



```js
返回链式编程的上一个状态 ： end()方法
// 结束当前链最近的一次过滤操作，并且返回匹配元素之前的一次状态。
参数：null    返回值：上一个状态
对象调用jQ方法后，返回的是jQ对象，才可以使用链式编程
作用：当链式编程断链时（调用方法后返回的不是jQ对象），可以调用，返回上一个状态
//链式编程代码
                //断链:对象调用方法,返回的不是当前的对象,再调用方法,调用不了,
                //解决断链--->恢复到断链之前的一个效果--修复断链
                //.end()方法恢复到断链之前的效果
```

```js
 $(this).prevAll().css("backgroundColor","yellow").end().nextAll().css("backgroundColor","blue");
```



### 1.3.2 each方法

~~~
有了隐式迭代，为什么还要使用each函数遍历？
大部分情况下是不需要使用each方法的，因为jQuery的隐式迭代特性。
如果要对每个元素做不同的处理，这时候就用到了each方法
~~~

- ##### each(function(index，element){})

  作用：遍历jQuery对象集合，为每个匹配的元素执行一个函数(函数可以不同)

  参数：index：表示当前元素在所有匹配元素中的索引号

  ​	   element：表示当前元素（DOM对象）

  $(selector).each(function(index,element){});

  ​

 es5中循环遍历的方法(数组的方法)循环遍历数组的每一项

- ##### foreach(function(element,index){})

  参数：匿名函数，数组每一项执行的操作

  获取：在传入的匿名函数中可以传入两个形参：value，index

  原数组不会发生变化

- ##### map(function(element,index){})

  参数：匿名函数，数组每一项执行的操作

  获取：在传入的匿名函数中可以传入两个形参：value，index

  原数组不会发生变化

  返回值：返回一个新的数组，

### 1.3.3 **多库共存（了解）******

此处多库共存指的是：jQuery占用了$ 和jQuery这两个变量。当在同一个页面中引用了jQuery这个js库，并且引用的其他库（或者其他版本的jQuery库）中也用到了$或者jQuery这两个变量，那么，要保证每个库都能正常使用，这时候就有了多库共存的问题。

 

// 模拟另外的库使用了 $ 这个变量

// 此时，就与jQuery库产生了冲突

var $ = { name : “itecast” };

 

解决方式：

// 作用：让jQuery释放对$的控制权，让其他库能够使用$符号，达到多库共存的目的。此后，只能使用jQuery来调用jQuery提供的方法

​	$.noConflict();

 

 

## 1.4 **jQuery插件机制**

jQuery这个js库，虽然功能强大，但也不是面面俱到包含所有的功能。

jQuery是通过插件的方式，来扩展它的功能：

当你需要某个插件的时候，你可以“安装”到jQuery上面，然后，使用。

当你不再需要这个插件，那你就可以从jQuery上“卸载”它。

（联想：手机软件，安装的app就好比插件，用的时候安装上，不用的时候卸载掉）

### 1.4.1 **第三方插件******

jQuery.color.js

​	animate()自定义动画：不支持背景的动画效果

  [animate动画支持的属性列表](http://www.w3school.com.cn/jquery/effect_animate.asp)

使用步骤：

1. 引入jQuery文件

2. 引入插件

3. 使用插件

### 1.4.2 **制作插件******

如何创建jQuery插件：

<http://learn.jquery.com/plugins/basic-plugin-creation/>

 

jQuery对象扩展方法

$.fn. pluginName = function() {};

 

 

### 1.4.3 **jQueryUI******

使用场景：网站的管理后台

 

jQueryUI专指由jQuery官方维护的UI（用户接口）方向的插件。

官方API：<http://api.jqueryui.com/category/all/>

其他教程：[jQueryUI教程](http://www.runoob.com/jqueryui/jqueryui-intro.html)

基本使用:

1. 引入jQueryUI的样式文件

2. 引入jQuery

3. 引入jQueryUI的js文件

4. 使用jQueryUI功能