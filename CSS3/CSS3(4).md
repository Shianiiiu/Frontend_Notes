# CSS3(4)

Created: 2020/11/09
Created by: ShianGee Hwang
Tags: flex布局, 响应式布局, 布局

# 十三、多列布局

![Untitled](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201109204419.png)

**兼容写法：**

```css
-moz-column-x:; /* Firefox */
-webkit-column-x:; /* Safari and Chrome */

/*IE不支持*/
```

- **column-count**

    规定元素应该被划分的列数

    ```css
    column-count: number|auto;
    ```

- **column-gap**

    规定列之间的间隔

    ```css
    column-gap: length|normal;
    ```

    length：把列间的间隔设置为指定的长度。
    normal：规定列间间隔为一个常规的间隔。

- **column-rule**

    设置列之间的宽度、样式和颜色规则

    一个简写属性，用于设置所有 column-rule-* 属性

    ```css
    column-rule: column-rule-width column-rule-style column-rule-color;
    ```

    - column-rule-style

        指定列之间的样式规则

        ```css
        column-rule-style: none|hidden|dotted|dashed|solid|double|groove|ridge|inset|outset;
        ```

        ![Untitled 1](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201109204445.png)

    - column-rule-width

        指定列之间的宽度规则

        ```css
        column-rule-width: thin|medium|thick|length;
        ```

        thin：指定一个细边框的规则；
        medium：定义一个中等边框规则t；?
        hick：指定一个粗边框的规则；
        length：指定宽度的规则

    - column-rule-color

        指定列之间的颜色规则

        ```css
        column-rule-color: color;
        ```

- **column-width**

    指定列的宽度

    ```css
    column-width: auto|length;
    ```

- **columns**

    指定列的宽度和数量

    ```css
    columns: column-width column-count;
    ```

# 十四、flex布局

CSS3 弹性盒（ Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。

引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。

## 1/ 弹性盒子定义方式

弹性容器通过设置 display 属性的值为 flex 或 inline-flex将其定义为弹性容器。

弹性子元素通常在弹性盒子内**一行显示**。默认情况每个容器只有一行。

```css
.box { display:flex; width:100%; height:300px; }
.box1 { width:300px;height:300px; }
```

## 2/ flex-direction

指定了弹性子元素在父容器中的位置。**决定主轴的方向**，此属性**作用于父容器**

```css
flex-direction: row | row-reverse | column | column-reverse
```

**row**：横向从左到右排列（左对齐），默认的排列方式。
**row-reverse**：反转横向排列（右对齐，从后往前排，最后一项排在最前面
**column**：纵向排列
**column-reverse**：反转纵向排列，从后往前排，最后一项排在最上面

![Untitled 2](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201109204502.png)

## 3/ justify-content

应用在弹性容器上，把弹性项沿着弹性容器的主轴线（main axis）对齐。此属性**作用于父容器**。

```css
justify-content: flex-start | flex-end | center | space-between | space-around
```

**flex-start**：紧凑方式左对齐
**flex-end**：紧凑方式右对齐
**center**：紧凑方式中对齐；如果剩余的自由空间是负的，则弹性项目将在两个方向上同时溢出
👉**space-between**：除了第1个和最后1个子元素外，其他子元素等分空白区域；如果剩余空间为负或者只有一个弹性项，则该值等同于flex-start

👉**space-around**：所有子元素等分空白区域，两边留有一半的间隔空间；如果剩余空间为负或者只有一个弹性项，则该值等同于center；*首尾两边和弹性容器之间留有一半的间隔*

![Untitled 3](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201109204516.png)

## 4/ align-items

 设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式。此属性**作用于父容器。**

```css
align-items: flex-start | flex-end | center | baseline | stretch
```

**flex-start**：纵向上对齐
**flex-end**：纵向下对齐
**center**：纵向垂中对齐

👉**baseline**：沿纵轴基线对齐；主要是内容基线对齐（联系英文字母的基线）
如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。

👉**stretch**：纵向拉伸对齐；(**默认值**)
如果指定侧轴大小的**属性值为'auto'**，（不指定内容的高度）则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。

如果项目未设置高度或设为auto，将占满整个容器的高度

![Untitled 4](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201109204534.png)

## 5/ flex-grow

定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。此属性**作用于子元素**。

```css
flex-grow： number
```

如果所有项目的flex-grow属性相同，则它们将等分剩余空间（如果有的话）

注意：和justify-content有相似之处，但是justify-content不会对空白区域进行扩展。**使用flex-grow内容不要定义宽度，那放大就无效。**

## 6/ flex

用于指定弹性子元素如何分配空间，此属性**作用于子元素**。

```css
flex: auto | initial | none | inherit | [ flex-grow ] || [ flex-shrink ] || [ flex-basis ]
```

**auto**：等价于 1 1 auto
**initia**l：等价于 0 1 auto
**none**：等价于 0 0 auto
**inherit**：继承父元素

flex属性是flex-grow, flex-shrink 和 flex-basis的简写，**默认值为0 1 auto**。后**两个属性可选**。

**flex可以带1-3个参数**

- 带一个参数
    - 无单位，被当作flex-grow（放大）的值
    - 带单位，被当作flex-basis（基本宽度）的值
    - auto（自动宽度）| initial（初始宽度）| none（无）
- 带两个参数

    第1个参数：必须是无单位的数值，被当作flex-grow（放大）的值

    - 第2个参数
        - 无单位，被当作flex-shrink（收缩比率）的值
        - 带单位，被当作flex-basis（基本宽度）的值
- 带三个参数

    第1个参数：必须是无单位的数值，被当作flex-grow（放大）的值

    第2个参数：必须是无单位的数值，被当作flex-shrink（收缩比率）的值

    第3个参数必须是一个有效的宽度值（带单位），被当作flex-basis（基本宽度）的值

---

👉*flex布局补充—>阮一峰教程*

[Flex 布局](https://www.notion.so/Flex-d75d9f6d0f5449988fec5a9ff6b058f4)

# 十五、响应式布局

![Untitled 5](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/20201109204551.png)

**Responsive Design 一个网站能够兼容多个终端**



### **响应式布局和自适应布局的区别**

1、响应式布局只开发一套代码，通过检测视口的分辨率，针对不同客户端在客户端做代码处理，来展现不同的布局和内容；
自适应需要开发多套界面，通过检测视口的分辨率，来诊断当前的设备，从而请求服务层，返回不同的界面

2、响应式布局等同于流动网格布局；自适应等同于使用固定分割点进行布局

3、自适应布局给出了更多的设计空间，只要考虑几种不同的状态就可以；
响应式需要考虑上百种不同的状态，虽然有些状态差异较小，但也要考虑

### 响应式布局开发实现方法

1. 媒体查询
2. 百分比布局
3. **rem布局**（相对于根节点（元素）html中的字号布局）
4. 视口单位布局（vw / vh）

### 响应式布局设计步骤

1. 设置`meta`标签
2. 通过媒体查询设置样式
3. 设置多种视图的宽度
    - 宽度需要使用百分比/rem/vw|vh等
    - 处理图片缩放
    - 其他属性处理
    如pre /iframe /video等，都要缩放大小；table，建议不用增加padding属性，低分辨率下使用内容居中操作