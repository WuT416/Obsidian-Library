使用方法
[https://juejin.im/post/5bc57e616fb9a05d396f3fc9](https://juejin.im/post/5bc57e616fb9a05d396f3fc9)

文档，各种配置
[https://iiunknown.gitbooks.io/iscroll-5-api-cn/content/init.html](https://iiunknown.gitbooks.io/iscroll-5-api-cn/content/init.html)

[https://www.cnblogs.com/zhuzhenwei918/p/6833559.html](https://www.cnblogs.com/zhuzhenwei918/p/6833559.html)

iscroll提倡简洁的DOM。**ul将会被滚动，且只有容器的第一个孩子节点被滚动，其他的孩子将会被忽略。**

**iscroll注意事项**

**1.只能滚动第一个节点，所以要用一层节点把要滚动的数据包裹起来**
**2.原理是数据的大小大于窗口，使超出的被隐藏，实现滚动。要注意数据与容器大小。**
**3.滚动可能提前发生，所以最好有延迟**

**例子**

```
//template部分
<div class="scroll-area">
      <ul class="ranking-list">
        <li v-for="(item,index) in rankingList" :key="index">
        </li>
      </ul>
    </div>
   
//script部分
  private myscroll: any = null;
  private mounted(): void {
    window.requestAnimationFrame(() => {
      this.myscroll = new IScroll('.scroll-area', {
        mouseWheel: true
      });
    });
  }
  
//style部分
.scroll-area {
  width: 100%;
  flex: 1;
  overflow: hidden;
  position: relative;
}
```
