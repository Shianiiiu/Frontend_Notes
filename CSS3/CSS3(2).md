## 六、CSS3平铺背景

1. **多重背景**
   backgroud：`背景色  背景图片  平铺方式  位置`，背景色  背景图片  平铺方式  位置,...

2. **backgroud-size**：设定背景图像的尺寸

   `background-size: length|percentage|cover|contain;

   `length`：设置背景图像的高度和宽度。第一个值设置宽度，第二个值设置高度。如果只设置一个值，则第二个值会被设置为 "auto"。
   `percentage`：以父元素的百分比来设置背景图像的宽度和高度。第一个值设置宽度，第二个值设置高度。如果只设置一个值，则第二个值会被设置为 "auto"。
    `cover`：把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。背景图像的某些部分也许无法显示在背景定位区域中。
   `contain`：把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。
   PS:contain和cover的区别，contain是保证图像的宽高中有一方能自适应背景区域，如果图像另外一方没有填满，则拼接（不设置no-repeat）；cover是图像足够大适应背景区域的宽高一方，如果背景区域另一方无法满足，可能导致图像有部分无法显示。

3. **backgroud-origin**：指定了背景图像的位置区域

   `background-origin: padding-box|border-box|content-box;`

   padding-box ： 背景图像相对于内边距框来定位。
   border-box : 背景图像相对于边框盒来定位。
   content-box ： 背景图像相对于内容框来定位。

4. **backgroud-clip**：属性规定背景的绘制区域
    `background-clip: border-box|padding-box|content-box;`
   border-box ：背景被裁剪到边框盒。
   padding-box ：背景被裁剪到内边距框。
   content-box ：背景被裁剪到内容框。

   PS：发现origin和clip的属性值是一样的，但是注意clip是**裁剪效果**。

## 七、CSS3颜色

1. **RGBA**
   `background-color: RGBA(R,G,B,A);`
   其中，A代表不透明度，取值范围：0-1的一个小数
   其他参数的取值范围：0-255 / 0-100%

2. **HSL**
   `background-color:hsl(h,s,l)`
   h: 色调  取值范围：0-360 
    0(或360) 表示红色，120表示绿色，240表示蓝色，也可取其他数值来指定颜色。
   s:  饱和度  取值范围：0-100%
   l:  亮度  取值范围：0-100%

   PS:通常用来设置遮罩层

3. **HSLA**

   `background-color:hsla(h,s,l,a)`
   h: 色调  取值范围：0-360 
    0(或360) 表示红色，120表示绿色，240表示蓝色，也可取其他数值来指定颜色。
   s:  饱和度  取值范围：0-100%
   l:  亮度  取值范围：0-100%
   a:  透明度  取值范围  0-1

4. **Opacity**
   调整元素的不透明度
   `opacity: value|inherit;`
   value:规定不透明度。从 0.0 （完全透明）到 1.0（完全不透明）。
   inherit:应该从父元素继承 opacity 属性的值。

   ```css
   兼容IE8及以下
   /*值的范围：1-100 */
   filter：alpha（opacity=0）;
   ```

## 八、CSS3渐变

1. **线性渐变**
   
（Internet Explorer 9 及更早版本的 IE 浏览器不支持线性渐变）
   
   ```css
   background-image: linear-gradient(direction/angle, color-stop1, color-stop2, ...);
   ```
   
   方向：默认是从上到下
   角度：比如45度，写成45deg
   
   > 角度是指水平线和渐变线之间的角度，逆时针方向计算。换句话说，0deg 将创建一个从下到上的渐变，90deg 将创建一个从左到右的渐变。
   >
   > 但是，请注意很多浏览器（Chrome、Safari、firefox等）的使用了旧的标准，即 0deg 将创建一个从左到右的渐变，90deg 将创建一个从下到上的渐变。换算公式 **90 - x = y** 其中 x 为标准角度，y为非标准角度。
   
   ![image-20201102134819655](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201102134827.png)
   
   颜色：单词/16进制/颜色函数
   重复线性渐变：`repeating-linear-gradient()` 函数用于重复线性渐变
   
2. **径向渐变**

   ```css
   background-image：radial-gradient(shape size at position, start-color, ..., last-color);
   ```

   默认情况下，渐变的中心是 center（表示在中心点），渐变的形状是 ellipse（表示椭圆形），渐变的大小是 farthest-corner（表示到最远的角落）。

   shape形状：circle / ellipse

   size尺寸：closest-side / farthest-side / closest-corner / farthest-corner

   position位置：center / bottom / top / at xx% xx%(具体的定位)

   重复的径向渐变：`repeating-radial-gradient()` 

3. **关于不均匀渐变百分比**

   百分比表示指定颜色的标准中心线位置，百分比之间是过渡色，如果百分比位置之间有重叠会失去渐变过渡色。

   ```css
   background: linear-gradient(red 10%, green 85%, blue 90%)
   ```

   > 其中：
   >
   > 10% 表示 red 的颜色中心线在线性渐变方向的 10% 的位置。
   >
   > 85% 表示 green 的颜色中心线在线性渐变方向的 85% 的位置。
   >
   > 90% 表示 blue 的颜色中心线在线性渐变方向的 90% 的位置。
   >
   > 10% 到 85% 是 red-green 的过渡色，85%-90% 是 green-blue 的过渡色。
   >
   > **background: linear-gradient(red 0%, green 50%, blue 50%)** 和 **background: linear-gradient(red 0%, green 50%, blue 10%)** 的效果一样。这可能是因为百分比位置之间有重叠才失去渐变过渡色，另渲染有一定先后顺序

4. **文字渐变**

   ```css
   background-image：linear-gradient();  /*如果只有单独这一句，只是设置背景*/
   -webkit-background-clip: text;
   -webkit-text-fill-color: transparent;
   ```

## 九、CSS3盒模型

 1. **box-sizing**

    ```css
    box-sizing: content-box（默认）|border-box|inherit;
    ```

    PS: 火狐和谷歌低版本需要加厂商铅坠。

    

    `content-box` : 宽度和高度分别应用到**元素的内容框**。

    在宽度和高度之外绘制元素的内边距和边框。

    

    `border-box` : 为元素设定的宽度和高度决定了**元素的边框盒**。

    通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高
    度。



