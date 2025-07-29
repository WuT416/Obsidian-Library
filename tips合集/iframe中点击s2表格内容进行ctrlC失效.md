
原因：
[1.Chrome](http://1.Chrome "http://1.Chrome")出于安全考虑，会限制未激活（非焦点）的 iframe 直接访问剪贴板 API 
2.学城通过iframe嵌入仪表板的情况下，点击s2单元格不会使iframe激活，点击其他地方可以

其他问题：
1.如何判断浏览器当前激活节点：
控制台输入document.activeElement
