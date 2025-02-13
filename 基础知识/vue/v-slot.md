[参考链接​](http://caibaojian.com/vue-slot.html)
[官方文档参考​](https://cn.vuejs.org/v2/guide/components-slots.html)

**什么是插槽**

子组件 HelloWorld
![[image (17).png]]

父组件
​![[image (18).png]]

网页展示
​![[image (19).png]]

这个时候 `<div>我是父组件</div>` 并不会展示出来，这个时候我们可以使用插槽slot
修改后子组件
![[image (20).png]]
​

修改子组件后网页
![[image (21).png]]
​

**插槽的作用**

让用户可以拓展组件，去更好地复用组件和对其做定制化处理

**默认插槽**

子组件
​![[image (22).png]]

父组件
![[image (23).png]]
​

如果父组件不提供任何插槽内容（甚至是空标签），子组件slot标签内的内容会显示，反之则会被父组件提供的插槽内容所覆盖。

**具名插槽**

有时候我们写了一个子组件，希望插槽的内容能够按我们希望的方式与顺序展示在子组件内容中。对于这样的情况，<slot> 元素有一个特殊的 attribute：name。这个 attribute 可以用来定义额外的插槽

子组件
![[image (24).png]]

父组件
![[image (25).png]]

展示效果
![[image (26).png]]