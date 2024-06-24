在一个简单的vue项目中使用路由，页面过多，会导致整个数组变得十分复杂，所以进行了一下简单的改造

改造前：
![[Pasted image 20240624171416.png]]

改造后：
![[Pasted image 20240624171436.png]]

router文件目录
![[Pasted image 20240624171511.png]]

主要知识点

用到了webpack的api--require方法，然后对目录里的文件做了一个正则匹配

参照：[https://blog.csdn.net/qq_42866164/article/details/102688831](https://blog.csdn.net/qq_42866164/article/details/102688831)