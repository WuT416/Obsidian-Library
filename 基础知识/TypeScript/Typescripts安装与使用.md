1.TypeScript 的命令行工具安装方法如下：

npm install -g typescript

2.编译一个 TypeScript 文件很简单：

tsc hello.ts

我们约定使用 TypeScript 编写的文件以 .ts 为后缀，用 TypeScript 编写 React 时，以 .tsx 为后缀。

3.**TypeScript 只会进行静态检查，如果发现有错误，编译的时候就会报错。TypeScript 编译的时候即使报错了，还是会生成编译结果**，我们仍然可以使用这个编译之后的文件。