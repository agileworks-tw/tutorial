# 練習題：將檔案放入暫存區，並模擬 git flow 流程。

1. 透過 `git checkout develop`
1. 透過 `git checkout -b feature/issue-1`
1. 透過 `echo "123" >> feature.md` 指令，新增一個檔案
1. 透過 `git add .` 指令，將檔案建立好索引
1. 透過 `git stash` 指令，將檔案暫時放置在暫存區
1. 透過 `git checkout master`
1. 透過 `git checkout -b hotfix/issue-2`
1. 透過 `echo "123" >> hotfix.md` 指令，新增一個檔案
1. 透過 `git commit -m 'I am hotfix'` 指令，新增一個送交紀錄
1. 透過 `git checkout feature/issue-1` 指令，回到 `feature/issue-1` 分支。
1. 透過 `git stash pop` 指令，將存擋取出。
1. 透過 `git add .` 指令，將檔案建立好索引
1. 透過 `git commit -m 'I am feature'` 指令，新增一個送交紀錄