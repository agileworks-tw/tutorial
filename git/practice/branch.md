### 練習題：branch

#### 情境：新增一個分支

#### Step1

```
vi start.sh

echo "Hello World" >> README.md && git add . && git commit -m 'init'
echo "1" >> m1.md && git add . && git commit -m 'm1'
echo "2" >> m2.md && git add . && git commit -m 'm2'

sh start.sh
```

#### Step2

1. 使用 `git branch hotfix/issue-1` 指令來建立 `hotfix/issue-1` 分支
1. 使用 `git checkout hotfix/issue-1` 指令來切換至 `hotfix/issue-1` 分支
1. 新增一個叫 `hotfix1.md` 檔案 `git add hotfix1.md`
1. 透過 `git commit -m 'h1'` 送交 commit
1. 確認已有新的分支產生 `git log --graph --oneline --decorate --all`

<!--
答案：

### step1

echo "Hello World" >> README.md && git add . && git commit -m 'init'
echo "1" >> m1.md && git add . && git commit -m 'm1'
echo "2" >> m2.md && git add . && git commit -m 'm2'

### step2

git checkout -b hotfix/issue-1
echo "hotfix1" >> hotfix1.md && git add . && git commit -m 'h1'


補充
git checkout -b develop
-->