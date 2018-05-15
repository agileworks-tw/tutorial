# git reset 指令

* --sort: 轉變為 uncommit 狀態
* --hard: 檔案會消失

### 使用情境

* 修正還未發佈的送交紀錄
* 將新增並已加入索引的檔案，還原到沒加入索引之前。

### 常用範例

| 範例                   | 說明     |
|----------------------|--------|
| git reset --sort HEAD  |        |
| git reset –-hard | 回覆到沒修改的狀態 |


### 語法結構

```
usage: git reset [--mixed | --soft | --hard | --merge | --keep] [-q] [<commit>]
   or: git reset [-q] <tree-ish> [--] <paths>...
   or: git reset --patch [<tree-ish>] [--] [<paths>...]

    -q, --quiet           be quiet, only report errors
    --mixed               reset HEAD and index
    --soft                reset only HEAD
    --hard                reset HEAD, index and working tree
    --merge               reset HEAD, index and working tree
    --keep                reset HEAD but keep local changes
    -p, --patch           select hunks interactively
    -N, --intent-to-add   record only the fact that removed paths will be added later
```