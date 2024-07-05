官网： [http://momentjs.cn/](http://momentjs.cn/)

文档： [http://momentjs.cn/docs/](http://momentjs.cn/docs/)

下载：npm install moment _--save_

引入
`import moment from 'moment';`

moment（）会得到一个对象，可以传入对象

格式：

```
moment()          什么都不传入，会得到当前日期
moment().format('YYYY-MM-DD')  年-Y 月-M 日-D 星期几-d   （星期日：0，星期一~星期六：1~6）
moment().add(i, 'd')  在当前基础上加i天
```
