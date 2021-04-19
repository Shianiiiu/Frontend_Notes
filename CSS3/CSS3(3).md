# CSS3(3)

Created: 2020/11/07
Created by: ShianGee Hwang
Tags: 动画过渡, 盒子变形

# 盒子的变形

## 1/CSS 2D变形

![Untitled](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201108161109.png)

## 2/CSS3 3D变形

- **perspective**

    让子元素获得透视效果

    ```css
    persperctive: none / number;
    ```

    主流浏览器都不支持，谷歌要加-webkit-，或者直接在长度后加单位

- **transform-style**

    规定如何在 3D 空间中呈现被嵌套的元素
    注意 ♦️：**该属性必须与 transform 属性一同使用，使用在父元素上**

    ```css
    transfrom-style: flat（默认值）|preserve-3d;
    ```

    > *flat* ：子元素将不保留其 3D 位置。
    *preserve-3d* ：子元素将保留其 3D 位置。

    ![Untitled 1](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201108161132.png)

    看一下效果😳

- **rotateZ**

    3D空间旋转指定的角度，沿着**垂直于Z轴的方向顺指针旋转**。

    ```css
    transform:rotateZ(130deg);
    ```

    类似：rotateX，rotateY

    元素围绕其 X / Y轴以给定的度数进行旋转

# CSS3过渡

- transition-property
- transition-duration
- transition-timing-function
- transition-delay

```css
transition: property duration timing-function delay;
```

注意❗：**请始终设置 transition-duration 属性**，否则时长为 0，就不会产生过渡效果。

Internet Explorer 10、Firefox、Opera 和 Chrome 支持 transition 属性。

Safari 支持替代的 -webkit-transition 属性。

注释：Internet Explorer 9 以及更早版本的浏览器不支持 transition 属性。

- **transition-property**

    规定设置过渡效果的 CSS 属性的名称

    ```css
    transition-property: none|all|property;
    ```

    指定property时，定义应用过渡效果的 CSS 属性名称列表，列表以逗号分隔

- **transition-duration**

    规定完成过渡效果需要多少秒或毫秒

    ```css
    transition-duration: time;
    ```

- **transition-timing-function**

    ```css
    transition-timing-function: linear|ease|ease-in|ease-out|ease-in-out|cubic-
    bezier(n,n,n,n);
    ```

    ![Untitled 2](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201108161215.png)

- **transition-delay**

    属性规定过渡效果何时开始，值以秒或毫秒计

    ```css
    transition-delay: time;
    ```

# CSS3动画

## 1/关键帧@keyframes

通过 @keyframes 规则，您能够创建动画。
创建动画的原理是，将一套 CSS 样式逐渐变化为另一套样式。
在动画过程中，您能够多次改变这套 CSS 样式。

以百分比来规定改变发生的时间，或者通过关键词 "from" 和 "to"，等价于 0% 和 100%。

0% 是动画的开始时间，100% 动画的结束时间。

为了获得最佳的浏览器支持，您应该始终定义 0% 和 100% 选择器。

## 2/动画animation

一个简写属性，用于设置六个动画属性

```css
animation: name duration timing-function delay iteration-count direction;
```

注意❗：**请始终设置 animation-duration 属性**，否则时长为 0，就不会产生过渡效果。

Internet Explorer 10、Firefox、Opera 支持 animation 属性。

Safari 和 Chrome 支持替代的 -webkit-animation 属性。

注释：Internet Explorer 9 以及更早版本的浏览器不支持 animation属性。

- **animation-name**

    规定需要绑定到选择器的 keyframe 名称
    来自于@keyframes定义的动画名

    ```css
    animation-name: keyframename|none;
    ```

- **animation-duration**

    规定完成动画所花费的时间，以秒或毫秒计

    ```css
    animation-duration: time;
    ```

- **animation-timing-function**

    规定动画的速度曲线，速度曲线用于使变化更为平滑

    ```css
    animation-timing-function: value;
    ```

    ![Untitled 3](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201108161230.png)

- **animation-delay**

    定义动画何时开始，值以秒或毫秒计

    注释：允许负值，-2s 使动画马上开始，但跳过 2 秒进入动画

    ```css
    animation-delay: time;
    ```

- **animation-iteration-count**

    定义动画的播放次数

    ```css
    animation-iteration-count: n|infinite;
    ```

- **animation-direction**

    定义是否应该轮流反向播放动画

    注释：如果把动画设置为只播放一次，则该属性没有效果。

    ```css
    animation-direction: normal|alternate;
    ```

    如果 animation-direction 值是 "alternate"，则动画会在奇数次数（1、3、5 等等）正常播放，而在偶数次数（2、4、6 等等）向后播放。

## 3/animation-play-state

规定动画正在运行还是暂停

注释：可以在 JavaScript 中使用该属性，这样就能在播放过程中暂停动画

```css
animation-play-state: paused|running（默认值）;
```

## 4/animation-fill-mode

规定动画在播放之前或之后，其动画效果是否可见

注释：其属性值是由逗号分隔的一个或多个填充模式关键词。

```css
animation-fill-mode : none | forwards | backwards | both;
```

![Untitled 4](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201108161251.png)

---

[关键帧动画.html](https://www.notion.so/html-7b09cdd431ee45b9acff178b25e0e5ef)

[CSS3-盒子变形-动画.pdf](https://www.notion.so/CSS3-pdf-9ea0128176314c7d831f9ac8b5d1c7c8)