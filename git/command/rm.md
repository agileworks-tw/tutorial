# git rm 指令

刪除檔案
### 常用範例

| 範例                | 說明            |
|-------------------|---------------|
| git rm README.txt | 將檔案從 repo 中刪除 |

### 語法結構

```
usage: git rm [<options>] [--] <file>...

    -n, --dry-run         dry run
    -q, --quiet           do not list removed files
    --cached              only remove from the index
    -f, --force           override the up-to-date check
    -r                    allow recursive removal
    --ignore-unmatch      exit with a zero status even if nothing matched
```