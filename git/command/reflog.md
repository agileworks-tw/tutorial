# git reflog 指令

追蹤變更軌跡

### 注意事項

這些更變軌跡紀錄並不會被同步到遠端 repo，僅限於本地端。

### 常用指令範例

| 範例                                                      | 說明       |
|---------------------------------------------------------|----------|
| git config --global gc.reflogExpire "never"             |          |
| git config --global gc.reflogExpireUnreachable "never"  |          |
| git config --global gc.reflogExpire "7 days"            |          |
| git config --global gc.reflogExpireUnreachable "7 days" |          |
| git reflog delete HEAD@{2}                              | 刪除更變軌跡   |
| git reflog                                              | 列表更變軌跡 |

### 語法結構

```
usage: git reflog [ show | expire | delete | exists ]
```