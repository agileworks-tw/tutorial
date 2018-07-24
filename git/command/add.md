# git add 指令

將檔案放入索引。將檔案備份到「物件儲存」中，使用 SHA1 算出名稱並且建立索引，將檔案放入準備狀態。
### 常用範例

| 範例                 | 說明  |
|--------------------|-----|
| git add README.txt |     |
| git add .          | 將資料先暫存到 staging area  |

### 語法結構

```
usage: git add [<options>] [--] <pathspec>...

    -n, --dry-run         dry run
    -v, --verbose         be verbose

    -i, --interactive     interactive picking
    -p, --patch           select hunks interactively
    -e, --edit            edit current diff and apply
    -f, --force           allow adding otherwise ignored files
    -u, --update          update tracked files
    -N, --intent-to-add   record only the fact that the path will be added later
    -A, --all             add changes from all tracked and untracked files
    --ignore-removal      ignore paths removed in the working tree (same as --no-all)
    --refresh             don't add, only refresh the index
    --ignore-errors       just skip files which cannot be added because of errors
    --ignore-missing      check if - even missing - files are ignored in dry run
```