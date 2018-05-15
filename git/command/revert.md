# git revert 指令

### 使用情境

* 修正已經發佈的送交紀錄，新增一個反向的 rollback 送交紀錄。

### 常用範例

| 範例              | 說明               |
|-----------------|------------------|
| git revert HEAD | 回到前一次 commit 的狀態 |

### 語法結構

```
usage: git revert [<options>] <commit-ish>...
   or: git revert <subcommand>

    --quit                end revert or cherry-pick sequence
    --continue            resume revert or cherry-pick sequence
    --abort               cancel revert or cherry-pick sequence
    -n, --no-commit       don't automatically commit
    -e, --edit            edit the commit message
    -s, --signoff         add Signed-off-by:
    -m, --mainline <n>    parent number
    --rerere-autoupdate   update the index with reused conflict resolution if possible
    --strategy <strategy>
                          merge strategy
    -X, --strategy-option <option>
                          option for merge strategy
    -S, --gpg-sign[=<key-id>]
                          GPG sign commit
```