[TOC]



### 1. 页面适配 

https://blog.csdn.net/weixin_45122120/article/details/100217970

https://juejin.im/post/6844903826512674829



### 2. 浏览器的回流与重绘 (Reflow & Repaint) 

https://juejin.im/post/6844903569087266823

KEY：Render Tree，回流，重绘

**回流必将引起重绘，重绘不一定会引起回流。**

#### 如何避免

CSS

- 避免使用`table`布局。
- 尽可能在`DOM`树的最末端改变`class`。
- 避免设置多层内联样式。
- 将动画效果应用到`position`属性为`absolute`或`fixed`的元素上。
- 避免使用`CSS`表达式（例如：`calc()`）。

JavaScript

- 避免频繁操作样式，最好一次性重写`style`属性，或者将样式列表定义为`class`并一次性更改`class`属性。
- 避免频繁操作`DOM`，创建一个`documentFragment`，在它上面应用所有`DOM操作`，最后再把它添加到文档中。
- 也可以先为元素设置`display: none`，操作结束后再把它显示出来。因为在`display`属性为`none`的元素上进行的`DOM`操作不会引发回流和重绘。
- 避免频繁读取会引发回流/重绘的属性，如果确实需要多次使用，就用一个变量缓存起来。
- 对具有复杂动画的元素使用绝对定位，使它脱离文档流，否则会引起父元素及后续元素频繁回流。



### 3. 实现水平居中垂直居中

https://juejin.im/post/6844903474879004680

* 水平居中：

  * 行内：```text-align:center; ```
  * 块级：```margin:0 auto; ```
  * flex ：

  ```
  .son{
      display: flex;
      justify-content: center;
  }
  ```

  

* 垂直居中：

  * 单行文本： line-height等于父元素；

  * 行内块级元素：

    ```
    .parent::after, .son{
        display:inline-block;
        vertical-align:middle;
    }
    .parent::after{
        content:'';
        height:100%;
    }
    ```
  
  * flex:
  
    ```
    .parent {
      display: flex;
      align-items: center;
    }
    ```
  
    



### 4. 当屏幕size减小时，调整样式

```html
      @media only screen and (max-width: 500px) {
        body {
          background-color: lightblue;
        }
      }
```



### 5. flex布局

https://zhuanlan.zhihu.com/p/25303493

布局借鉴：

 https://codepen.io/LandonSchropp/pen/KpzzGo 

http://www.ruanyifeng.com/blog/2015/07/flex-examples.htm

https://magic-akari.github.io/solved-by-flexbox/



块元素div用display: flex

行内元素可以用display:inline-flex

⚠️设置了flex布局后，子元素的 float、clear、vertical-align 的属性将会失效。

flex实际上就是三行语句的缩写：

- `flex-grow`
- `flex-shrink`
- `flex-basis`

常用方法：

- `flex: initial` - Equivalent to ```flex: 0 1 auto```.
- `flex: auto` - Equivalent to ```flex: 1 1 auto```.
- `flex: none` - Equivalent to ```flex: 0 0 auto```.
- `flex: <positive-number>` - Equivalent to ```flex: <positive-number> 1 0```.





### 6. 前端选择器

[前端布局必须了解的css选择器](https://juejin.im/post/5eaf64276fb9a0435749c23a#comment)

只有当内容为空时才会显示的css

```html
  <div class="test">
    <div class="emptyone"></div>
    <div class="emptyone">noempot</div>
  </div>
  
  .test {
    .emptyone:empty {
      height:10px;
      background: aqua; 
    }
  }
```

效果如图：![image-20200630144829287](/Users/mac/Desktop/日报/Vuex.assets/image-20200630144829287.png)



### 7. 不同尺寸的使用

https://www.w3schools.com/cssref/css_units.asp

* 绝对尺寸 px

* 相对尺寸 em %

  





