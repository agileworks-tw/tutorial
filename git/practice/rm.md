# 練習題：rm

### 情境：誤新增了一筆不該放入 repo 的檔案，需要被移除。

1. 透過 `touch system.log`，新增一筆 log。
1. 透過 `git add .`，將更變建立索引。
1. 透過 `git commit -m 'add log'`，新增 commit 紀錄。
1. 透過 `git rm system.log` 指令，刪除 system.log 檔案
1. 透過 `git commit -m 'remove log'` 指令，將刪除檔案的紀錄送交給 repo。
1. 透過 `touch .gitignore` 指令，新增 .gitignore 檔案。
1. 編輯 .gitignore 檔案，加入 *.log
1. 透過 `git add .`，將更變建立索引。
1. 透過 `git commit -m 'add .gitignore file'`，新增 commit 紀錄。

<!-- 
解答

touch system.log
git add .
git commit -m 'add log'
git rm system.log
git commit -m 'remove log'
touch .gitignore

git add . && git commit -m 'add .gitignore file'
-->