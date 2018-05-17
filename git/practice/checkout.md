# 練習題：commit

### 情境：還原尚未 commit 的最新的變動

1. 編輯 README.md
1. 透過 `git checkout -- README.md` 指令，還原修改的內容

<!--
答案：

### step1

echo "Hello World" >> README.md && git add . && git commit -m 'init'
echo "alincode" >> README.md


### step2

git checkout -- README.md
-->