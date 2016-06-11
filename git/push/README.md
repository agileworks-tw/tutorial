# push

使用 `push` 在遠端數據庫上共享本地端數據庫的修改記錄

## 已有設定遠端檔案庫

`git push origin master`


## 新增遠端檔案庫

`git remote add origin <server>`


## 練習將 local 版本控制 push 到 GitHub 上面的個人 repository

### 建立 local 的 git 版本控制專案
1. 新增資料夾 git-tutorial
2. 進入 git-tutorial 資料夾
2. 新增檔案 README.md
3. 執行 `git init` 初始化專案
4. 執行 `git add .` 加入所有變更的檔案
5. 執行 git commit -m 'init'
6. 完成第一個版本控制

### 建立 remote 版本控制專案

1. 在 GitHub 上面建立 git-tutorial 新的專案
2. 複製 GitHub 上的 repo url，EX: https://github.com/username/git-tutorial.git
3. 執行 `git remote add origin https://github.com/username/git-tutorial.git`
4. 執行 `git push -u origin master` 將目前的 commit push 到 GitHub
5. 重新整理網頁 <https://github.com/username/git-tutorial> 確認已有檔案新增至 GitHub
