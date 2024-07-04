报错内容
```
Failed at the lint script. npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
```


出现这样的原因在于使用了husky，并且配置了"precommit": "npm run lint"

因此会在你git commit的时候执行npm run lint 也就是eslint --ext .js src test

如果报错的话，会返回非0，从而组织代码commit。

因此有两种方式解决：

执行npm run lint， 根据提示修改错误，如果是其他人的报错，请求别人协助（推荐）

git commit -m '' -n 强制推送