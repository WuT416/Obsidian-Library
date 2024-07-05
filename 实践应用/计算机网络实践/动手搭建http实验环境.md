## 安装OpenResty

OpenResty ，它是基于 Nginx 的一个“强化包”，里面除了 Nginx 还有一大堆有用的功能模块，不仅支持 HTTP/HTTPS，还特别集成了脚本语言 Lua 简化 Nginx 二次开发，方便快速地搭建动态网关，更能够当成应用容器来编写业务逻辑。

1. 需要homebrew，安装
```
#先安装Mac的homebrew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. homebrew 安装 OpenResty
```
#使用homebrew安装OpenResty
brew install openresty/brew/openresty
```

3. git clone项目源码，clone到自己的目录下
`git clone https://github.com/chronolaw/http_study`

![[Pasted image 20240705174321.png]]

## 安装wireshark抓包工具
![[Pasted image 20240705174348.png]]

## 在终端中进入www目录下，熟悉命令

```
cd http_study/www/    #脚本必须在www目录下运行，才能找到nginx.conf
./run.sh start        #启动实验环境
./run.sh list         #列出实验环境的Nginx进程
./run.sh reload       #重启实验环境
./run.sh stop         #停止实验环境
```

## 启动实验环境
  ./run.sh start 

## 点开wireshark
点开wireshark，双击wifi或者loopback“环回”地址。
![[Pasted image 20240705174519.png]]

## 浏览器打开http://localhost
![[Pasted image 20240705174601.png]]
![[Pasted image 20240705174610.png]]

这时再回头去看 Wireshark，应该会显示已经抓到了一些数据，就可以用鼠标点击工具栏里的“停止捕获”按钮告诉 Wireshark“到此为止”，不再继续抓包。

记得停止实验环境
