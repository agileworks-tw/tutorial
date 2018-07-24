# 練習題：新增兩個送交紀錄

1. 透過 `mkdir commit` 指令，新增一個資料夾叫 `commit`
2. 透過 `git init` 指令，進行專案初始化。
1. 透過 `echo "Hello World" >> README.md` 指令，在資料夾中，新增一個檔案叫 `README.md`
1. 透過 `git add .` 指令，將所有更變加入 index 中
1. 透過 `git commit -m 'init'` 指令，將更變送交給 git
1. 透過 `echo 123 >> README.md` 指令，編輯 `README.md`
1. 透過 `git add .` 指令，將所有更變加入 index 中
1. 透過 `git commit -m 'update readme'` 指令，將更變送交給 git
1. 完成第一個版本控制範例


<!--
答案：

echo "Hello World" >> README.md && git add . && git commit -m 'init'
echo 123 >> README.md && git add . && git commit -m 'update readme'

-->