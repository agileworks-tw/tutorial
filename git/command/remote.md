# git remote 指令

### 常用範例

| 範例                                                     | 說明                |
|--------------------------------------------------------|-------------------|
| git remote                                             | 顯示遠端來源名稱          |
| git remote -v                                          | 顯示遠端來源詳細資訊        |
| git remote add origin http://git.xx.com.tw/project.git | 加入遠端來源            |
| git remote rename origin origin2                       | 修改遠端來源的名字         |
| git remote rm origin2                                  | 刪除叫 origin2 的遠端連接 |

### 語法結構

```
usage: git remote [-v | --verbose]
   or: git remote add [-t <branch>] [-m <master>] [-f] [--tags | --no-tags] [--mirror=<fetch|push>] <name> <url>
   or: git remote rename <old> <new>
   or: git remote remove <name>
   or: git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
   or: git remote [-v | --verbose] show [-n] <name>
   or: git remote prune [-n | --dry-run] <name>
   or: git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)...]
   or: git remote set-branches [--add] <name> <branch>...
   or: git remote get-url [--push] [--all] <name>
   or: git remote set-url [--push] <name> <newurl> [<oldurl>]
   or: git remote set-url --add <name> <newurl>
   or: git remote set-url --delete <name> <url>

    -v, --verbose         be verbose; must be placed before a subcommand
```