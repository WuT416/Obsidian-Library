## 问题记录

修改了一个问题引起了错误

### 修改前：

定义一个数据
```
private testObject: any = {
	test1: []
};
```

赋值操作
```
@Watch('getCountIndexList', { immediate: true, deep: true })
private getCountIndexListH(): void {
	this.testObject.test1 = [...this.getAnalysisIndexList, ...this.getCountIndexList];
}

```

使用
```
allIndexList: [
	{
		required: true,
		validator: (rule, value, callback) => {
			this.$nextTick(() => {
				const flag = this.testObject.test1.some((item: Index) => {
					return item.indexType === IndexTypeEnum.indexTypeOrigin;
				});
				if (!flag) {
					return callback(new Error('必填'));
				}
				callback();
			});
		},
		trigger: 'change',
	},
], 
```


状态
![[Pasted image 20240621154659.png]]
### 修改后：

定义
 `private testObject: Index[] = [];`

赋值操作
```
@Watch('getCountIndexList', { immediate: true, deep: true })
private getCountIndexListH(): void {
   this.testObject = [...this.getAnalysisIndexList, ...this.getCountIndexList];
}
```

使用
```
allIndexList: [
	{
		required: true,
		validator: (rule, value, callback) => {
			this.$nextTick(() => {
				const flag = this.testObject.some((item: Index) => {
					return item.indexType === IndexTypeEnum.indexTypeOrigin;
				});
				if (!flag) {
					return callback(new Error('必填'));
				}
				callback();
			});
		},
		trigger: 'change',
	},
], 
```


状态
![[Pasted image 20240621154837.png]]
## 排查过程

输出发现在validator中

修改后的this.testObject为空数组，获取不到数据

由于this指针变化，获取不到testObject

## 解决方案

将validator提出来，避免this指针混乱
```
allIndexList: [
	{
		required: true,
		validator: this.validatorAllIndexList,
		trigger: 'change',
	},
],

 private validatorAllIndexList(rule, value, callback) {
	this.$nextTick(() => {
		const flag = this.testObject.some((item: Index) => {
			return item.indexType === IndexTypeEnum.indexTypeOrigin;
		});
		if (!flag) {
			return callback(new Error('必填'));
		}
		callback();
	});
}        
```

