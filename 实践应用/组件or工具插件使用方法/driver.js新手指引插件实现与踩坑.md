链接：[https://github.com/kamranahmedse/driver.js](https://github.com/kamranahmedse/driver.js)

# 问题一：

Animate为true，有动画情况下，背景不可点，高亮是可点的

解决方案：

强制将，pointer-events改为none
![[Pasted image 20240705173109.png]]
链接：[https://github.com/kamranahmedse/driver.js/issues/171](https://github.com/kamranahmedse/driver.js/issues/171)

# 问题二：

Animate为true，会出现高亮空白的状况
![[Pasted image 20240705173137.png]]
解决方案：
![[Pasted image 20240705173149.png]]
无法解决，弃用动画

[https://github.com/kamranahmedse/driver.js/issues/31](https://github.com/kamranahmedse/driver.js/issues/31)


# 问题三：

Animate为false，会出现叠加层可穿透点击的情况，这bug仅限于移动端

解决方案：
![[Pasted image 20240705173226.png]]

在新手指引启动时，禁用整个页面，新手指引结束后，启用

[https://github.com/kamranahmedse/driver.js/issues/247](https://github.com/kamranahmedse/driver.js/issues/247)