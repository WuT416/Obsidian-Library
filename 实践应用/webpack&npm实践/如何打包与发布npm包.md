## 打包

1. 新建一个包
![[Pasted image 20240704151859.png]]

2. 新增一个index.js与初始化npm包
`npm init`
![[Pasted image 20240704151931.png]]

3. 查询是否有这个包名，公开包
 `npm search draggle`
 
 4. 安装babel、webpack、jest。npm install自动生成package-lock
 `npm i babel-core babel-loader babel-plugin-add-module-exports babel-preset-env eslint webpack webpack-cli clean-webpack-plugin babel-jest jest` 
 ![[Pasted image 20240704152040.png]]
 
 5. 添加一个文件webpack.config.js
```
const path = require('path');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
    mode: 'production', // 环境
    entry: './index.js', // 入口文件
    output: {
        path: path.resolve(__dirname, './dist'), // 输出文件夹
        filename: 'mytest.js', // 文件名称
        libraryTarget: 'umd', // 打包方式
        globalObject: 'this', // 全局对象
        library: 'mytest', // 类库名称
    },
    plugins: [
        new CleanWebpackPlugin(), // 清除上一次打包内容
    ],
    externals: {
        'vue': 'Vue', // 不参与打包编译
    },
}
```

6. 新建文件夹lib，在下面的index.js中添加主要方法
```
function add(a, b) {
  return a + b;
}

function reduce(a, b) {
  return a - b;
}

function multiply(a, b) {
  return a * b;
}

const test = {
    add,
    reduce,
    multiply,
}

module.exports = test;
```

7. 在根目录的index.js下引用方法
```
const mytest = require('./lib/index');
module.exports = mytest;
```

8. 设定打包方法
![[Pasted image 20240704152337.png]]

9. 运行npm run build进行打包
![[Pasted image 20240704152354.png]]
dist是我们的output，自动生成

10. - 新建.gitignore文件，忽视nodemodules
`node_modules`
![[Pasted image 20240704152445.png]]


## 测试

这里使用jest来进行测试。文件命名规则：<测试名称>.test.js。
1. 新建一个测试文件add.test.js。
    ```
    // ./my.test.js
    const add = require('./dist/mytest').add;
    
    test('adds 1 + 2 to equal 3', () => {
        expect(add(1,2)).toBe(3);
    })
    ```

2. 修改package代码
```
"scripts": {
    "test": "jest",
    "build": "webpack"
  },
```

3. 运行npm run test
![[Pasted image 20240704152635.png]]
测试浏览器环境

4. 新建一个example文件夹，写入node.js用于测试node环境，运行node ./example/node.js查看一下，如果输出3说明测试成功。
```
// ./example/node.js
const fegqTestAdd = require('../dist/mytest').add;
console.log(fegqTestAdd(1,2)); // 3
```

5. 写入browser.html用于测试游览器环境。npm install -g live-server。运行live-server --port=4001启动一个http服务，F12打开控制台输出3说明测试成功。
  
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>browser测试</title>
</head>
<body>
    <h2>fegq-test测试</h2>
    <script src="../dist/mytest.js"></script>
    <script>
        let result = mytest.add(1,2);
        console.log(result); // 3
    </script>
</body>
</html>
```


## 发布

`npm publish`

![[Pasted image 20240704152854.png]]
package.json中加入代码改为公开
```
"publishConfig": {
    "access": "public",
    "registry": "https://registry.npmjs.org/"
  },
```
重新发布
![[Pasted image 20240704152927.png]]