1. v-text
    1. **预期**：string
        
    2. **详细**：
        
        更新元素的 textContent。如果要更新部分的 textContent，需要使用 {{ Mustache }} 插值。
        
2. v-html
    
    1. **预期**：string
        
    2. **详细**：
        
        更新元素的 innerHTML。**注意：内容按普通 HTML 插入 - 不会作为 Vue 模板进行编译**。如果试图使用 v-html 组合模板，可以重新考虑是否通过使用组件来替代。
        
3. v-show
    
    1. **预期**：any
        
    2. **用法**：
        
        根据表达式之真假值，切换元素的 display CSS property。
        
        当条件变化时该指令触发过渡效果。
        
4. v-if
    
    1. **预期**：any
        
    2. **用法**：
        
        根据表达式的值的 truthiness 来有条件地渲染元素。在切换时元素及它的数据绑定 / 组件被销毁并重建。如果元素是 <template>，将提出它的内容作为条件块。
        
        当条件变化时该指令触发过渡效果。
        
5. v-else
    
    1. **不需要表达式**
        
    2. **限制**：前一兄弟元素必须有 v-if 或 v-else-if。
        
    3. **用法**：
        
        为 v-if 或者 v-else-if 添加“else 块”。
        
6. v-else-if
    
    1. **类型**：any
        
    2. **限制**：前一兄弟元素必须有 v-if 或 v-else-if。
        
    3. **用法**：
        
        表示 v-if 的“else if 块”。可以链式调用。
        
7. v-for
    
    1. **预期**：Array | Object | number | string | Iterable (2.6 新增)
        
    2. **用法**：
        
        基于源数据多次渲染元素或模板块。此指令之值，必须使用特定语法 alias in expression，为当前遍历的元素提供别名：另外也可以为数组索引指定别名 (或者用于对象的键)：v-for 的默认行为会尝试原地修改元素而不是移动它们。要强制其重新排序元素，你需要用特殊 attribute key 来提供一个排序提示：
        
8. v-on
    
    - **缩写**：@
        
    - **预期**：Function | Inline Statement | Object
        
    - **参数**：event
        
    - **修饰符**：
        
        - .stop - 调用 event.stopPropagation()。
            
        - .prevent - 调用 event.preventDefault()。
            
        - .capture - 添加事件侦听器时使用 capture 模式。
            
        - .self - 只当事件是从侦听器绑定的元素本身触发时才触发回调。
            
        - .{keyCode | keyAlias} - 只当事件是从特定键触发时才触发回调。
            
        - .native - 监听组件根元素的原生事件。
            
        - .once - 只触发一次回调。
            
        - .left - (2.2.0) 只当点击鼠标左键时触发。
            
        - .right - (2.2.0) 只当点击鼠标右键时触发。
            
        - .middle - (2.2.0) 只当点击鼠标中键时触发。
            
        - .passive - (2.3.0) 以 { passive: true } 模式添加侦听器
            
    - **用法**：
        
        绑定事件监听器。事件类型由参数指定。表达式可以是一个方法的名字或一个内联语句，如果没有修饰符也可以省略。
        
        用在普通元素上时，只能监听**[**原生 DOM 事件**](https://developer.mozilla.org/zh-CN/docs/Web/Events)**。用在自定义元素组件上时，也可以监听子组件触发的**自定义事件**。
        
        在监听原生 DOM 事件时，方法以事件为唯一的参数。如果使用内联语句，语句可以访问一个 $event property：v-on:click="handle('ok', $event)"。
        
        从 2.4.0 开始，v-on 同样支持不带参数绑定一个事件/监听器键值对的对象。注意当使用对象语法时，是不支持任何修饰器的。
        
9. v-bind
    
    1. **缩写**：:
        
    2. **预期**：any (with argument) | Object (without argument)
        
    3. **参数**：attrOrProp (optional)
        
    4. **修饰符**：
        
        - .prop - 作为一个 DOM property 绑定而不是作为 attribute 绑定。(**[差别在哪里？](https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html#answer-6004028)**)
            
        - .camel - (2.1.0+) 将 kebab-case attribute 名转换为 camelCase。(从 2.1.0 开始支持)
            
        - .sync (2.3.0+) 语法糖，会扩展成一个更新父组件绑定值的 v-on 侦听器。
            
    5. **用法**：
        
        动态地绑定一个或多个 attribute，或一个组件 prop 到表达式。
        
        在绑定 class 或 style attribute 时，支持其它类型的值，如数组或对象。可以通过下面的教程链接查看详情。
        
        在绑定 prop 时，prop 必须在子组件中声明。可以用修饰符指定不同的绑定类型。
        
        没有参数时，可以绑定到一个包含键值对的对象。注意此时 class 和 style 绑定不支持数组和对象。
        
10. v-model
    
    1. **预期**：随表单控件类型不同而不同。
        
    2. **限制**：
        
        - <input>
            
        - <select>
            
        - <textarea>
            
        - components
            
    3. **修饰符**：
        
        - .lazy - 取代 input 监听 change 事件
            
        - .number - 输入字符串转为有效的数字
            
        - .trim - 输入首尾空格过滤
            
    4. **用法**：
        
        在表单控件或者组件上创建双向绑定。细节请看下面的教程链接。
        
11. v-slot
    
    1. **缩写**：#
        
    2. **预期**：可放置在函数参数位置的 JavaScript 表达式 (在支持的环境下可使用解构)。可选，即只需要在为插槽传入 prop 的时候使用。
        
    3. **参数**：插槽名 (可选，默认值是 default)
        
    4. **限用于**
        
        - <template>
            
        - 组件 (对于一个单独的带 prop 的默认插槽)
            
    5. **用法**：
        
        提供具名插槽或需要接收 prop 的插槽。
        
12. v-pre
    
    1. **不需要表达式**
        
    2. **用法**：
        
        跳过这个元素和它的子元素的编译过程。可以用来显示原始 Mustache 标签。跳过大量没有指令的节点会加快编译。
        
13. v-cloak
    
    1. **不需要表达式**
        
    2. **用法**：
        
        这个指令保持在元素上直到关联实例结束编译。和 CSS 规则如 [v-cloak] { display: none } 一起用时，这个指令可以隐藏未编译的 Mustache 标签直到实例准备完毕。
        
14. v-once
    
    1. **不需要表达式**
        
    2. **详细**：
        
        只渲染元素和组件**一次**。随后的重新渲染，元素/组件及其所有的子节点将被视为静态内容并跳过。这可以用于优化更新性能。