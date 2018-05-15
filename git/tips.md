# 實用小技巧

### 新增空的資料夾


```
.gitkeeper
```

### 救回誤刪的檔案

```
# 查看已刪除的檔案
git ls-files -d

# 將已刪除的檔案還原
git ls-files -d | xargs git checkout —
```

### 救回誤刪的分支

若你不小心移除了分支或是其他參照，你可以使用 `git reflog` 指令來還原。

### 快速尋找臭蟲

* 善用 grep
* 善用 blame 文件逐行追溯
* 善用 bisect 二分查找