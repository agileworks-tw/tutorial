# git branch CRUD

git branch --all                                                                                                                                ```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

### 名稱

* 絕對名稱
* 參照名稱

```
refs/head
refs/remotes
refs/tags
```

### 常用範例

| 範例                     | 說明                        |
|------------------------|---------------------------|
| git branch dev         | 新增 dev 分支                 |
| git branch             | 列出 local 分支               |
| git branch -r          | 列出遠端分支                    |
| git branch -a          | 列出所有分支                    |
| git branch -m dev dev2 | 修改分支名稱                    |
| git branch -d dev2     | 刪除分支                      |
| git branch -D dev2     | 強迫刪除分支 (即使分支，還沒被 merge 過) |

### 相關聯指令

| 範例                  | 說明        |
|---------------------|-----------|
| git push origin dev | 發佈 dev 分支 |

### 語法結構

```
usage: git branch [<options>] [-r | -a] [--merged | --no-merged]
   or: git branch [<options>] [-l] [-f] <branch-name> [<start-point>]
   or: git branch [<options>] [-r] (-d | -D) <branch-name>...
   or: git branch [<options>] (-m | -M) [<old-branch>] <new-branch>
   or: git branch [<options>] [-r | -a] [--points-at]
```
