### 如何使用查询参数query
```
// 存入
this.$router.push({
	path: this.$route.path,
	query: {
		...this.$route.query,
		message: this.message
	}
})
// 获取
this.message = this.$router.query.message
```

        
如何使用
```
// 存入 
this.$router.push({
	   name: 'detail',
	   params: {
		 shopid: item.id
	   }
});
// 获取
this.$route.params.shopid
```

        
### 相似点

- 可以利用查询参数实现刷新后在原分页
- 复杂的组件关系中可以方便传递数据
### 不同点
    
- 使用query的话url上会出现字段，不安全。使用params只会出现字段名
- params相对应的是name query相对应的是path