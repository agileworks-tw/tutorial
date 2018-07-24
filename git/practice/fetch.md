# 練習題：fetch

### 情境：透過 fetch 指令取得最新送交紀錄

#### 前置環境

```
git clone https://github.com/agileworks-tw/git-hello-world
```

#### 講師操作

```
vi README.md
git add .
git commit -m 'add my name'
git push
```

#### 學員操作

```
git fetch origin
git log --graph --oneline --decorate --all
git merge origin/master
git log --graph --oneline --decorate --all
```