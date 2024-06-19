### 背景
页面echart图形中，包括图例和横纵轴在内的文字都会出现模糊的状况。

### 过程
出现这样的原因是因为ECharts 默认使用 Canvas 渲染。Canvas 是基于像素的即时模式图形系统，依赖分辨率。放大的时候图形会出现锯齿等等。

## 方案

方案一：仍然采用canvas绘制，设置像素比
```
var myChart = echarts.init(document.getElementById('chart'), null, {devicePixelRatio: 2.5});
```
自己调试感觉效果一般

方案二：改为svg绘制
```
this.myChart = this.$echarts.init(document.getElementById('myChart'), null, {renderer: 'svg'})
```
效果很好