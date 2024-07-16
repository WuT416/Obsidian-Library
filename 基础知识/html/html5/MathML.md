MathML 是数学标记语言，是一种基于XML（标准通用标记语言的子集）的标准，用来在互联网上书写数学符号和公式的置标语言

```
<math xmlns="http://www.w3.org/1998/Math/MathML">
            <mrow>
                <msup><mi>4</mi><mn>2</mn></msup>
                <mo>+</mo>
                <msup><mi>5</mi><mn>3</mn></msup>
                <mo>></mo>
                <msup><mi>2</mi><mn>2</mn></msup>
            </mrow>
</math>
```

math为顶层元素
<msup>表示上标
<mi>标识符，也就是说，象'n'或'p'这样单个字符显示成斜体，象"mod"这样的字符串则按普通格式(竖式)显示。其中，mi中的'i'是英文identifier的首字母。
<mn>数字
<mrow>分组后的子表达式
<mo>运算符 Operator

```
<math xmlns="http://www.w3.org/1998/Math/MathML">
   <mrow>           
      <mrow>
         <msup>
            <mi>x</mi>
            <mn>2</mn>
         </msup>
         <mo>+</mo>
         <mrow>
            <mn>4</mn>
            <mo>⁢</mo>
            <mi>x</mi>
         </mrow>
         <mo>+</mo>
         <mn>4</mn>
      </mrow>
      <mo>=</mo>
      <mn>0</mn>
   </mrow>
</math>
```
参考文档：

[https://developer.mozilla.org/zh-CN/docs/Web/MathML/Element](https://developer.mozilla.org/zh-CN/docs/Web/MathML/Element)
[https://www.twle.cn/l/yufei/html5/html-v5-mathml.html](https://www.twle.cn/l/yufei/html5/html-v5-mathml.html)