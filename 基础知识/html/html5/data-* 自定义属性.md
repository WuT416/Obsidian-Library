示例：

```
<li data-id="111111" data-name="lvzhenbang" data-email="[lvzhenbang@outlook.com](mailto:lvzhenbang@outlook.com)" data-github="[https://github.com/lvzhenbang](https://github.com/lvzhenbang)">lvzhenbang</li>
```

使用

```
// 用户信息的操作按钮
var oBtn = document.getElementById('opt-btn');
// 删除按钮
var delBtn = document.getElementById('delte-btn');
// 获得信息
var id = oBtn.getAttribute('data-id');
// 改变数据信息
delBtn.setAttribute('data-id', id);
// 改变删除按钮的数据信息，html5原生的API dataset来reading/writing
delBtn.setAttribute.id = id;
```

局限：

data-* 虽然好用，但它也只是一个attribute，只能存储字符串。