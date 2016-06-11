# reset

## 放棄所有 local file change

```
git fetch origin
git reset --hard origin/master
```


## reset 的類型及主要使用的場合
* 復原修改過的索引的狀態(mixed)
* 徹底取消最近的提交(hard)
* 只取消提交(soft)
