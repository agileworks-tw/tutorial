# 練習題：解決衝突

## 情境設定

### 建立一個裸容器

```
cd ~/workspace/git-sample
mkdir hello.git
cd hello.git
git init --bare
```

### 模擬 john 的行為

```
cd ..
git clone ~/workspace/git-sample/hello.git john-hello
cd ~/workspace/git-sample/john-hello
git config user.email "john@demo.com"
git config user.name "john"
echo "123" >> hello.txt
git add .
git commit -m 'create hello file'
```

### 模擬 lily 的行為

```
cd ~/workspace/git-sample/
git clone ~/workspace/git-sample/hello.git lily-hello
cd ~/workspace/git-sample/lily-hello
git config user.email "lily@demo.com"
git config user.name "lily"
```

### john 編輯檔案

vi hello.txt

```
123 456
```

```
git add .
git commit -m 'add 456'
git push -u origin master
```

### lily 編輯檔案

vi hello.txt

```
123 789
```

```
git add .
git commit -m 'add 789'
git push -u origin master
```

### 解決衝突

```
git pull
git diff
# vi 編輯衝突
git add .
git commit
git push -u origin master
```