## 背景
从外部拖入：https://jbaysolutions.github.io/vue-grid-layout/zh/guide/10-drag-from-outside.html
这个在vue3版本中无法跑通，自己实现

## 代码
```
import { Ref } from 'vue'

interface DragParams {

id: string

layout: Ref<{

items: Array<{

i: string

w: number

h: number

x: number

y: number

}>

}>

gridlayout: any

addChart: (chart, positon) => void

}

  

const useDrag = (params: DragParams) => {

let { id, gridlayout, layout, addChart } = params

let mouseXY = { x: 0, y: 0 }

let DragPos = { x: 0, y: 0, w: 12, h: 6, i: '' }

  

const handleDrag = (item) => {

const parentRect = document.getElementById(`grid-layout-content-${id}`)?.getBoundingClientRect()

if (!parentRect) return

const layoutArr = layout.value.items

  

// 是否拖拽到该画布中

let mouseInGrid =

mouseXY.x > parentRect.left &&

mouseXY.x < parentRect.right &&

mouseXY.y > parentRect.top &&

mouseXY.y < parentRect.bottom

  

if (mouseInGrid && layoutArr.findIndex((item) => item.i === 'drop') === -1) {

// 直接修改layout，待改进

// 增加临时元素，仅用作占位符样式

layoutArr.push({

x: (layoutArr.length * 2) % 12,

y: layoutArr.length + 12,

w: item?.defaultSize?.w || 6,

h: item?.defaultSize?.h || 6,

i: 'drop' // 表临时元素

})

DragPos.w = item?.defaultSize?.w || 6

DragPos.h = item?.defaultSize?.h || 6

}

let index = layoutArr.findIndex((item) => item.i === 'drop')

if (index !== -1) {

// 计算鼠标在 gridlayout 中的相对位置

const mouseInGridX = mouseXY.x - parentRect.left

const mouseInGridY = mouseXY.y - parentRect.top

  

// 计算占位符的位置

const placeholderX = Math.floor(mouseInGridX / (parentRect.width / gridlayout.colNum))

const placeholderY = Math.floor(mouseInGridY / gridlayout.rowHeight)

  

// 更新鼠标在占位符的位置

DragPos.x = placeholderX

DragPos.y = placeholderY

// 鼠标在布局中移动，更新占位部分

if (mouseInGrid === true) {

// 占位部分

gridlayout.dragEvent('dragstart', 'drop', DragPos.x, DragPos.y, DragPos.h, DragPos.w)

// 鼠标推算出的位置由于组件碰撞画布大小等受限，并不等于最后位置，更新DragPos的正确位置

DragPos.x = layoutArr[index].x

DragPos.y = layoutArr[index].y

}

// 鼠标已经移出布局，则撤回一个拖拽增加的行为。

if (mouseInGrid === false) {

gridlayout.dragEvent('dragend', 'drop', DragPos.x, DragPos.y, DragPos.w, DragPos.h)

// 直接修改layout，待改进

let index = layoutArr.findIndex((item) => item.i === 'drop')

layoutArr.splice(index, 1)

}

}

}

  

const handleDragEnd = (item) => {

const parentRect = document.getElementById(`grid-layout-content-${id}`)?.getBoundingClientRect()

if (!parentRect) return

const layoutArr = layout.value.items

const mouseInGrid =

mouseXY.x > parentRect.left &&

mouseXY.x < parentRect.right &&

mouseXY.y > parentRect.top &&

mouseXY.y < parentRect.bottom

  

if (mouseInGrid) {

gridlayout?.dragEvent('dragend', 'drop', DragPos.x, DragPos.y, 1, 1)

  

// 直接修改layout，待改进

let index = layoutArr.findIndex((item) => item.i === 'drop')

layoutArr.splice(index, 1) // 删除临时元素，仅用作占位符样式

// 确定添加

addChart(item, { x: DragPos.x, y: DragPos.y })

}

}

return {

mouseXY,

handleDrag,

handleDragEnd

}

}

  

export default useDrag
```
