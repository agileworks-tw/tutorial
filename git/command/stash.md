# git stash 指令

暫存

### 使用情境

* 通常用於臨時必須要切換到其他分支，但現在工作做到一半還不能 commit 時，就先把修改存起來，切到其他分支事情做完之後，再回來把修改取出來，繼續剛剛未完成的工作。

### 常用範例

| 範例                          | 說明           |
|-----------------------------|--------------|
| git stash                   | 暫時儲存當前目錄        |
| git stash list              | 列出所有暫存區的資料   |
| git stash pop               | 取出最新的一筆, 並移除 |
| git stash clear             | 把 stash 都清掉  |
| git stash drop <stash_name> | 清掉單一筆暫存      |


### 語法結構

```
usage: git stash list [<options>]
   or: git stash show [<stash>]
   or: git stash drop [-q|--quiet] [<stash>]
   or: git stash ( pop | apply ) [--index] [-q|--quiet] [<stash>]
   or: git stash branch <branchname> [<stash>]
   or: git stash [save [--patch] [-k|--[no-]keep-index] [-q|--quiet]
                       [-u|--include-untracked] [-a|--all] [<message>]]
   or: git stash clear
```