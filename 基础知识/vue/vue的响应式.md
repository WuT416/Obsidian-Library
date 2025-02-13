**1.什么是vue的响应式**

数据模型仅仅是普通的 JavaScript 对象。而当你修改它们时，视图会进行更新。

**2.如何实现响应式**

当你把一个普通的 JavaScript 对象传入 Vue 实例作为 data 选项，Vue 将遍历此对象所有的 property，并使用 **[Object.defineProperty](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)** 把这些 property 全部转为 **[getter/setter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Working_with_Objects#%E5%AE%9A%E4%B9%89_getters_%E4%B8%8E_setters)**。这些 getter/setter 对用户来说是不可见的，但是在内部它们让 Vue 能够追踪依赖，在 property 被访问和修改时通知变更。每个组件实例都对应一个 **watcher** 实例，它会在组件渲染的过程中把“接触”过的数据 property 记录为依赖。之后当依赖项的 setter 触发时，会通知 watcher，从而使它关联的组件重新渲染。

**3.响应式的限制**

由于 JavaScript 的限制，Vue **不能检测**数组和对象的变化。尽管如此我们还是有一些办法来回避这些限制并保证它们的响应性。

**对于对象：**

Vue 无法检测 property 的添加或移除。由于 Vue 会在初始化实例时对 property 执行 getter/setter 转化，所以 property 必须在 data 对象上存在才能让 Vue 将它转换为响应式的。

对于已经创建的实例，Vue 不允许动态添加根级别的响应式 property。但是，可以使用 Vue.set(object, propertyName, value) 方法向嵌套对象添加响应式 property。例如，对于：
`Vue.set(vm.someObject, 'b', 2)`

您还可以使用 vm.$set 实例方法，这也是全局 Vue.set 方法的别名：
`this.$set(this.someObject,'b',2)`

有时你可能需要为已有对象赋值多个新 property，比如使用 Object.assign() 或 _.extend()。但是，这样添加到对象上的新 property 不会触发更新。在这种情况下，你应该用原对象与要混合进去的对象的 property 一起创建一个新的对象。
```
// 代替 `Object.assign(this.someObject, { a: 1, b: 2 })`

this.someObject = Object.assign({}, this.someObject, { a: 1, b: 2 })
```


**对于数组：**

Vue 不能检测以下数组的变动：

1. 当你利用索引直接设置一个数组项时，例如：vm.items[indexOfItem] = newValue
    
2. 当你修改数组的长度时，例如：vm.items.length = newLength
    

解决第一类问题：

```
// Vue.set

Vue.set(vm.items, indexOfItem, newValue)
```

```
// Array.prototype.splice

vm.items.splice(indexOfItem, 1, newValue)
```

```
vm.$set(vm.items, indexOfItem, newValue)
```


解决第二类问题
```
vm.items.splice(newLength)
```
