## 一、CSS3的主要新特性

>   1）选择器
>   2）阴影
>   3）形状转换（2d,3d）
>   4）变形
>   5）动画（过度动画，帧动画）
>   6）边框
>   7）多重背景
>   8）反射
>   9）文字
>   10）颜色（rgba/hsl/hsla)
>   11）滤镜
>   12）弹性布局
>   13）多列布局
>   14）盒模型
>   15）web字体
>   16）媒体查询

## 二、CSS3属性前缀

**兼容不同浏览器，添加厂商前缀**

> Trident内核：主要代表为IE浏览器  
>
>  Gecko内核：主要代表为Firefox 
>
>   Blink内核：主要代表为Chrome和Opera ——>是webkit的一个分支   
>
> Webkit内核：产要代表为Chrome和Safari

>  Trident内核：前缀为`-ms-`  ——>IE  
>
>  Gecko内核：前缀为`-moz-`  ——>Firefox   
>
>  Blink内核：前缀为`-o-`  ——>对应Opera   
>
>  Webkit内核：前缀为`-webkit`-  ——>Chrome / Safari

**PS**：Blink内核的Chrome浏览器是支持CSS3的 

## 三、CSS3选择器

> 减少class和id属性的使用

![image-20201026204224182](https://gitee.com/shianiiiu/picgo_bed/raw/master/img/css3._1.png)

**PS** : 1、`:root` 匹配html标签，和body选择器效果一样
		2、:checked 只在Opera中有效，比如表单提交中的checkbox、select列表  选中的元素
		3、::selection 对被选中的文本，如鼠标左右滑动选中  :warning: 注意有两个冒号！
		……

## 四、CSS3文本

1. **文本阴影**

   主流浏览器都支持

   `text-shadow：h-shadow  v-shadow  blur  color`

   属性值：

   ​	h-shadow {number} ：必需。水平阴影的位置。允许负值。
   ​	v-shadow {number} : 必需。垂直阴影的位置。允许负值。
   ​	blur {number} ：可选。模糊的距离。
   ​	color {color} ：可选。阴影的颜色。

2. **文本自动换行**
    `word-wrap : normal / break-word`
   属性值：

   normal ：只在允许的断字点换行（浏览器保持默认处理）。
   ​break-word : 在长单词或 URL 地址内部进行换行。

3. **单词拆分**
    `word-break : normal / break-all / keep-all`
    属性值：
    normal ：使用浏览器默认的换行规则。
    break-all : 允许在单词内换行。
    keep-all ：只能在半角空格或连字符处换行。

4. **文本溢出**
    1）单行文本溢出（重要）

    ​	`text-overflow: clip|ellipsis|string;`
    属性值：

    clip ：修剪文本。
    ellipsis : 显示省略符号来代表被修剪的文本。
    string ：使用给定的字符串来代表被修剪的文本。

    PS：处理文字溢出一般样式 

    ​		width : ;  给出宽度
    ​		white-space: nowrap; // 不折行
    ​		text-overflow: ellipsis;
    ​		-ms-text-overflow: ellipsis;	
    ​		overflow：hidden;

    2）多行文本溢出（主要是谷歌支持）
    	display: -webkit-box;
    	-webkit-box-orient: vertical;
    	-webkit-line-clamp: 3;  //显示的行数
    	overflow: hidden;

## 五、CSS3边框

1. 圆角边框
   `border-radius: 1-4 length|% / 1-4 length|%;`

   注释：按此顺序设置每个 radii 的四个值。如果省略 bottom-left，则与 top-right 相同。如果省略 bottom-right，则与 top-left 相同。如果省略 top-right，则与 top-left 相同。

   属性值：
   	length ：定义圆角的形状。
   	% : 以百分比定义圆角的形状

   示例：
   	示例一：

   ​	`border-radius:20px;`

   ​	等价
   ​	`border-top-left-radius:20px;`
   ​	`border-top-right-radius:20px;`
   ​	`border-bottom-right-radius:20px;`
   ​	`border-bottom-left-radius:20px;`

   ​	示例二：
   ​	`border-radius:20px **30px** 40px;`

   ​	等价
   ​	`border-top-left-radius:20px;`
   ​	`border-top-right-radius:30px;`
   ​	`border-bottom-right-radius:40px;`
   ​	`border-bottom-left-radius:30px;`

   ​	PS: 主要是理解四个参数的指示方向

   行成圆示例：
   	`border-radius:50%;`
   	或者
   	`border-radius: half of 容器的宽高;`
   	这里的前提设置：假设给一个div，然后宽高要设置相同

2. 边框阴影(IE9以上支持)
   `box-shadow: h-shadow v-shadow [blur] [spread] [color] [inset];`
   box-shadow: 水平偏移距离  垂直偏移距离  [模糊]  [阴影的尺寸]  [颜色]  [inset]

   inset ：将外部阴影 (outset) 改为内部阴影

3. 边框图片(IE11.0及以上版本支持)
   `border-image: source slice width outset repeat`
   border-image：图片路径  图片边框向内偏移  图片边框的宽度  边框图像区域超出边框的量  图像边框是否应平铺(repeat)、铺满(round)或拉伸(stretch)





 