1.**Vuex是数据状态管理框架，主要做到了数据和视图层的解耦**

而已经有EventBus我们为什么还要使用Vuex这个问题上

我们仔细思考一下，当我们使用EventBus时，我们A控件给B控件和C控件传递数据后，B控件经过处理又要修改传递过来数据，继续通知A控件和C控件修改数据，这样在C文件中就要多处监听A和B的EventBus。这样当有关于数据传递有bug时，我们就很难追溯到底是哪一个环节出了问题。

伴随着我们业务的复杂程度变高，视图的复杂度也会随之升高，所以此时通过Vuex来对数据和视图层解耦就显得十分必要。

Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式**。（Vuex 可以帮助我们管理共享状态）

什么是“状态管理模式”？

让我们从一个简单的 Vue 计数应用开始：

```
new Vue({
  // state
  data () {
    return {
      count: 0
    }
  },
  // view
  template: `
    <div>{{ count }}</div>
  `,
  // actions
  methods: {
    increment () {
      this.count++
    }
  }
})
```
这个状态自管理应用包含以下几个部分：

- **state**，驱动应用的数据源；
    
- **view**，以声明方式将 **state** 映射到视图；
    
- **actions**，响应在 **view** 上的用户输入导致的状态变化。
    

但是，当我们的应用遇到**多个组件共享状态**时，单向数据流的简洁性很容易被破坏：

- 多个视图依赖于同一状态。
    
- 来自不同视图的行为需要变更同一状态。
    

2.每一个 Vuex 应用的核心就是 store（仓库）

- Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。
    

- 你不能直接改变 store 中的状态。改变 store 中的状态的唯一途径就是显式地**提交 (commit) mutation**。
    

3.state

Vuex 使用**单一状态树**——是的，用一个对象就包含了全部的应用层级状态。至此它便作为一个“唯一数据源 (**[SSOT](https://en.wikipedia.org/wiki/Single_source_of_truth)**)”而存在。这也意味着，每个应用将仅仅包含一个 store 实例。单一状态树让我们能够直接地定位任一特定的状态片段，在调试的过程中也能轻易地取得整个当前应用状态的快照。

参考文档：[https://vuex.vuejs.org/zh/guide/](https://vuex.vuejs.org/zh/guide/)