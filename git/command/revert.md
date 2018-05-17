# git revert 指令

新增還原的送交紀錄

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

### 練習題

情境：還原某一個已經發佈的 commit

```
echo "Hello World" >> README.md && git add . && git commit -m 'init'
echo "1" >> 1.md && git add . && git commit -m 'c1'
echo "2" >> 2.md && git add . && git commit -m 'c2'
echo "3" >> 3.md && git add . && git commit -m 'c3'
git reflog
```

output:

```
3f1e27b HEAD@{0}: commit: c3
e15d462 HEAD@{1}: commit: c2
d9968dd HEAD@{2}: commit: c1
106cbc4 HEAD@{3}: commit (initial): init
```

```
git revert HEAD@{1}
git log --oneline
```