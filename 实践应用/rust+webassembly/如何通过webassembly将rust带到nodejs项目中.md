## 总结

通过wasm-pack将rust代码打包成npm模块，发布为npm包，node项目正常引用和使用

## 1.创建rust包
![[Pasted image 20240619104730.png]]
rust包，此处使用的是现成的包，克隆的https://github.com/rustwasm/wasm-pack-template，当然我们也可以使用cargo自己创建一个项目，这个模板就是使用cargo管理的。

## 2.工具代码
![[Pasted image 20240619104858.png]]
写了两个很简单的函数

## 3.npm包打包与发布

这里我走了一个弯路，刚开始用的命令如下
`wasm-pack build`
结果发布之后引入一直无效，翻了一下wasm-pack的官网，原来这个工具为不同环境准备了不同的命令语句
![[Pasted image 20240619105000.png]]
正确的打包代码
`wasm-pack build --target nodejs`
最后就是大家都知道的npm publish 发布（包名在Cargo.toml中修改）
![[Pasted image 20240619105038.png]]
打包成功
![[Pasted image 20240619105116.png]]
## 4.使用

这之后就跟使用一个正常的npm包没有太大区别
引入
`"wasm-test-pkg-vivian":"^0.2.1"`
使用

```
import * as wasm from 'wasm-test-pkg-vivian'

console.log(wasm.divide(3,1))
```

