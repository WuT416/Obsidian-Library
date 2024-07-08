- align-content: stretch | center | flex-start | flex-end | space-between | space-around | initial | inherit
- 
    - 在弹性容器内的各项没有占用交叉轴上所有可用的空间时对齐容器内的各项（垂直）。
        
    - stretch：默认值。元素被拉伸以适应容器。各行将会伸展以占用剩余的空间。如果剩余的空间是负数，该值等效于'flex-start'。在其它情况下，剩余空间被所有行平分，以扩大它们的侧轴尺寸。
        
    - center：元素位于容器的中心。各行向弹性盒容器的中间位置堆叠。各行两两紧靠住同时在弹性盒容器中居中对齐，保持弹性盒容器的侧轴起始内容边界和第一行之间的距离与该容器的侧轴结束内容边界与第最后一行之间的距离相等。（如果剩下的空间是负数，则各行会向两个方向溢出的相等距离。）
        
    - flex-start：元素位于容器的开头。各行向弹性盒容器的起始位置堆叠。弹性盒容器中第一行的侧轴起始边界紧靠住该弹性盒容器的侧轴起始边界，之后的每一行都紧靠住前面一行。
        
    - flex-end：元素位于容器的结尾。各行向弹性盒容器的结束位置堆叠。弹性盒容器中最后一行的侧轴起结束界紧靠住该弹性盒容器的侧轴结束边界，之后的每一行都紧靠住前面一行。
        
    - space-between：元素位于各行之间留有空白的容器内。各行在弹性盒容器中平均分布。如果剩余的空间是负数或弹性盒容器中只有一行，该值等效于'flex-start'。在其它情况下，第一行的侧轴起始边界紧靠住弹性盒容器的侧轴起始内容边界，最后一行的侧轴结束边界紧靠住弹性盒容器的侧轴结束内容边界，剩余的行则按一定方式在弹性盒窗口中排列，以保持两两之间的空间相等。
        
    - space-around：元素位于各行之前、之间、之后都留有空白的容器内。各行在弹性盒容器中平均分布，两端保留子元素与子元素之间间距大小的一半。如果剩余的空间是负数或弹性盒容器中只有一行，该值等效于'center'。在其它情况下，各行会按一定方式在弹性盒容器中排列，以保持两两之间的空间相等，同时第一行前面及最后一行后面的空间是其他空间的一半。
        
    - initial：设置该属性为它的默认值
        
    - inherit：从父元素继承该属性。
        
- all: initial | inherit | unset
    
    - initia：修改所有元素属性或父元素的值为其初始化值
        
    - inherit：修改所有元素属性或父元素的值为其父元素的值
        
    - unset：修改所有元素属性或父元素的值为其父元素的值(如果有继承)或其初始值
        
- animation
    
    - 动画
        
- appearance: normal | icon | window | button | menu | field
    
    - 允许您使元素看上去像标准的用户界面元素。
        
    - normal：正常呈现元素
        
    - icon：作为一个小图片的呈现元素
        
    - window：作为一个视口呈现元素
        
    - button：作为一个按钮，呈现元素
        
    - menu：作为一个用户选项设定呈现元素选择
        
    - field：作为一个输入字段呈现元素
        
- backface-visibility: visible | hidden
    
    - visibility：背面是可见的。
        
    - hidden：背面是不可见的。
        
- background:bg-color bg-image position / bg-size bg-repeat bg-origin bg-clip bg-attachment initial | inherit
    
    - 背景缩写属性可以在一个声明中设置所有的背景属性。各值之间用空格分隔，不分先后顺序。可以只有其中的某些值。
        
- background-attachment：scroll | fixed | local | initial | inherit
    
    - 设置背景图像是否固定或者随着页面的其余部分滚动。
        
    - scroll：背景图片随着页面的滚动而滚动，这是默认的。
        
    - fixed：背景图片不会随着页面的滚动而滚动。
        
    - local：背景图片会随着元素内容的滚动而滚动。
        
    - initial：设置该属性的默认值。
        
    - inherit：指定 background-attachment 的设置应该从父元素继承。
        
- background-blend-mode: normal | multiply | screen | overlay | darken | lighten | color-dodge | saturation | color | luminosity
    
    - 定义了背景层的混合模式（图片与颜色）。
        
    - normal：默认值。设置正常的混合模式。
        
    - multiply：正片叠底模式。
        
    - screen：滤色模式。
        
    - overlay：叠加模式。
        
    - darken：变暗模式。
        
    - lighten：变亮模式。
        
    - color-dodge：颜色减淡模式。
        
    - saturation：饱和度模式。
        
    - color：颜色模式。
        
    - luminosity：亮度模式。
        
- background-clip: border-box | padding-box | content-box
    
    - 指定背景绘制区域。
        
    - border-box：默认值。背景绘制在边框方框内（剪切成边框方框）。
        
    - padding-box：背景绘制在衬距方框内（剪切成衬距方框）。
        
    - content-box：背景绘制在内容方框内（剪切成内容方框）。
        
- background-color：颜色名称or值 | transparent | inherit
    
    - 颜色：十六进制颜色、RGB颜色、RGBA颜色、HSL色彩、HSLA颜色、预定义/跨浏览器的颜色名称
        
    - transparent：透明
        

- background-image：url(_'URL'_) | none | linear-gradient() | radial-gradient() | repeating-linear-gradient() | repeating-radial-gradient() | inherit
    
    - url(_'URL'_)：图像的URL
        
    - none：无图像背景会显示。
        
    - linear-gradient()：创建一个线性渐变的 "图像"(从上到下)
        
    - radial-gradient()：用径向渐变创建 "图像"。 (center to edges)
        
    - repeating-linear-gradient()：创建重复的线性渐变 "图像"。
        
    - repeating-radial-gradient()：创建重复的径向渐变 "图像"
        
    - inherit：指定背景图像应该从父元素继承
        
- background-origin: padding-box | border-box | content-box
    
    - 指定background-position属性应该是相对位置。如果背景图像background-attachment是"固定"，这个属性没有任何效果。
        
    - padding-box：背景图像填充框的相对位置
        
    - border-box：背景图像边界框的相对位置
        
    - content-box：背景图像的相对位置的内容框
        
- background-position：left top | left center | left bottom | right top | right center | right bottom | center top | center center | center bottom | x% y% | xpos ypos | inherit
    
    - 设置背景图像的起始位置。对于这个工作在Firefox和Opera，background-attachment必须设置为 "fixed（固定）".
        
    - left/right/center top/bottom/center：如果仅指定一个关键字，其他值将会是"center"
        
    - x% y%：第一个值是水平位置，第二个值是垂直。左上角是0％0％。右下角是100％100％。如果仅指定了一个值，其他值将是50％。 。默认值为：0％0％
        
    - xpos ypos：第一个值是水平位置，第二个值是垂直。左上角是0。单位可以是像素（0px0px）或任何其他 [CSS单位](https://www.runoob.com/try/css-units.html)。如果仅指定了一个值，其他值将是50％。你可以混合使用％和positions
        
    - inherit：指定background-position属性设置应该从父元素继承
        
- background-repeat：repeat | repeat-x | repeat-y | no-repeat | inherit
    
    - 设置如何平铺对象的 background-image 属性。默认情况下，重复background-image的垂直和水平方向。
        
    - repeat：背景图像将向垂直和水平方向重复。这是默认。
        
    - repeat-x：只有水平位置会重复背景图像
        
    - repeat-y：只有垂直位置会重复背景图像
        
    - no-repeat：background-image不会重复
        
- background-size: _length_ | _percentage_ | cover | contain
    
    - 指定背景图片大小。
        
    - length：设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为 **auto**(自动)
        
    - percentage：将计算相对于背景定位区域的百分比。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)"
        
    - cover：此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小。
        
    - contain：此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小。
        
- border：border-width | border-style | border-color | inherit
    
    - 缩写边框属性设置在一个声明中所有的边框属性。可以设置的属性分别（按顺序）：border-width, border-style,和border-color。如果上述值缺少一个没有关系，例如border：＃FF0000;是允许的。
        
- border-bottom：border-bottom-width | border-bottom-style | border-bottom-color.
    
    - 缩写属性设置一个声明中所有底部边框属性。可以设置的属性分别（按顺序）：border-bottom-width, border-bottom-style,和border-bottom-color。如果上述值缺少一个没有关系，例如border-bottom：＃FF0000;是允许的
        
- border-bottom-color：同border-color
    
- border-bottom-left-radius: _length_ | _%_ [_length_ | _%_]
    
    - 属性定义左下角边框的形状。
        
- border-bottom-right-radius
    
    - 属性定义右下角边框的形状。
        
- border-bottom-style：同border-style
    
    - 属性设置元素底部边框样式。
        
- border-bottom-width：同border-width
    
    - 属性设置元素的底部边框宽度。**注意**务必先声明border-style属性才可以设置border-bottom-width属性。元素必须有边框，你才可以改变宽度。
        
- border-collapse ：collapse | separate | inherit
    
    - 属性设置表格的边框是否被合并为一个单一的边框，还是象在标准的 HTML 中那样分开显示。
        
    - collapse：如果可能，边框会合并为一个单一的边框。会忽略 border-spacing 和 empty-cells 属性
        
    - separate：默认值。边框会被分开。不会忽略 border-spacing 和 empty-cells 属性。
        
- border-color：颜色名称or值 | transparent | inherit
    
    - 设置一个元素的四个边框颜色。此属性可以有一到四个值。一个值上下左右，两个值上下、左右，三个值上、左右、下，四个值上右下左。
        
- border-image：border-image-source | border-image-slice | border-image-width | border-image-outset | border-image-repeat
    
    - 缩写属性，省略的值即为他们的默认值。
        
- border-image-source: none | _image_
    
    - border-image-source属性指定要使用的图像，而不是由border-style属性设置的边框样式。
        
    - none：没有图像被使用
        
    - _image：_边框使用图像的路径
        
- border-image-slice: _number_ | _%_ | fill
    
    - number：数字表示图像的像素（位图图像）或向量的坐标（如果图像是矢量图像）
        
    - %：百分比图像的大小是相对的：水平偏移图像的宽度，垂直偏移图像的高度
        
    - fill：保留图像的中间部分
        
- border-image-width：_number_ | _%_ | auto
    
    - border-image -width属性指定图像边界的宽度。border-image -width的4个值指定用于把border图像区域分为九个部分。他们代表上，右，底部，左，两侧向内距离。如果第四个值被省略，它和第二个是相同的。如果也省略了第三个，它和第一个是相同的。如果也省略了第二个，它和第一个是相同的。负值是不允许的。
        
- border-left：border-left-width | border-left-style | border-left-color
    
    - 简写属性把左边框的所有属性设置到一个声明中。可以按顺序设置如下属性： border-left-width, border-left-style, and border-left-color。如果不设置其中的某个值，也不会出问题，比如 border-left:solid #ff0000; 也是允许的。
        
- border-radius: _1-4 length_|_%_ / _1-4 length_|_%_
    
    - 每个半径的四个值的顺序是：左上角，右上角，右下角，左下角。如果省略左下角，右上角是相同的。如果省略右下角，左上角是相同的。如果省略右上角，左上角是相同的。
        
    - _length：_定义弯道的形状。
        
    - %：使用%定义角落的形状。
        
- border-spacing ：_length length |_ inherit
    
    - 属性设置相邻单元格的边框间的距离（仅用于"边框分离"模式）。
        
    - _length length：_规定相邻单元的边框之间的距离。使用 px、cm 等单位。不允许使用负值。
        
        - 如果定义一个 length 参数，那么定义的是水平和垂直间距。
            
        - 如果定义两个 length 参数，那么第一个设置水平间距，而第二个设置垂直间距。
            
- border-style
    
    - border-style属性设置一个元素的四个边框的样式。此属性可以有一到四个值。