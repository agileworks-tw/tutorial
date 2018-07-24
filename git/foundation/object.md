# 認識 Git 物件


### 物件型態

#### blob 物件

實際檔案內容
#### tree 物件

```
git write-tree
git cat-file -p 6c5285378c5f9294109815b927ee46177ed7f0c6
```

```
100644 blob f3b9a76bc4e9ccad8e613a8f00d279ae023e81d9    .gitignore
040000 tree 2ce507750fe9d51b9a587934cadb8dcb4d08e358    .vscode
100644 blob 95e9b0b25b5295ea09df687ce87921dc359fbcb0    LICENSE
100644 blob 5302934326ee2082005ebf0a7cd3a932a75353a0    README.md
100644 blob ee0e01483aefc3326749380bd9f47f13181cb14c    SUMMARY.md
040000 tree e3a43292c1c3b9d75731ffa28e2f8b287654efc3    command
040000 tree 4af7150c15ed99abc02e935619af322da8620903    foundation
040000 tree 671d79384113b2b73961f254d25013bfe89d25e3    git-flow
100644 blob 9464f843f5dc01ede201ee872218db64eb905dc1    github.md
040000 tree ca88d0944c8ac48c7750eed3ab534f6f1911969f    mise
040000 tree 05f4dc2fd37ead780727bd55d122c23b204f3cab    practice
040000 tree a4006ed3288ce93305ebd8bb79be648c2955d101    prepare
100644 blob cf61a2ddec9e7b2d7e73e1400b1ff0c2ff24d31a    resource.md
040000 tree a54bcc2e0a588a95dac720af08e400245120f9ee    setup
100644 blob c9ceb128cc0a241fd3d088fa9f14972916502f40    tips.md
```

#### commit 物件 (送交物件)

```
git log --oneline
git cat-file -p eb3fba1
```

```
tree 81745419c7ba83f077eaaf86bd2fafd3fb9b8b64
parent f512170b13fa45e065c219fad3a89843b0002b4e
author alincode <alincode@gmail.com> 1526312241 +0800
committer alincode <alincode@gmail.com> 1526312241 +0800

update
```

* 樹狀物件的名稱，該物件顯示檔案的關聯
* 前一個 commit 是誰
* 新版本作者的姓名以及新版本修改的時間
* 送交者的姓名及送交時間
* 此修訂版本 commit 時，留下的描述

#### tag 物件

```
git rev-parse v0.0.1
git cat-file -p d8044b536a827ea34e638a3da76dae9740922896
```

```
tree 16ae2442a6869cb7be3aeec47129721218d8074d
parent fb7f269f31cd9fe29712ed2a4b7f4cde208ed6e3
parent 8ccde2dc957c45a2575ec1b385cfda93c9ed1b60
author Your Name <you@example.com> 1526307625 +0000
committer Your Name <you@example.com> 1526307625 +0000

Merge branch 'dev'
```

### 物件儲存

* 當 Git 要儲存一個物件時，它使用內容雜湊演算值，而不是檔案名稱。若有兩個存在不同目錄，但內容相同的檔案，兩個檔案的 SHA1 會相同。
* SHA1 的前兩位數，會作為 `git/object/前兩位數` 的放置位置。

#### find .git

* object：實際儲存檔案內容的位置
* hook
* logs：分支的 commit 紀錄
* refs：分支的最後一筆 commit sha code
```
.git/objects/af
.git/objects/af/f6388cffe192b412dfca52ddeee7a7ebd8961e
```

#### git ls-files -s

列出目前工作目錄的檔案

```
100644 aff6388cffe192b412dfca52ddeee7a7ebd8961e 0       hello.txt
```


#### git write-tree

```
bb9e55860a20ae3a1c441d5e2d8a5e0261a3f2ff
```

#### git cat-file -p cbfd7a8e6c7bd0eec9f524b42bdce9ff31bac2e3

將內容反組譯

```
100644 blob aff6388cffe192b412dfca52ddeee7a7ebd8961e    hello.txt
100644 blob 14be0d41c639d701e0fe23e835b5fe9524b4459d    hello2.txt
```

### Git 內部檔案

find .git


```
.git
.git/branches
.git/COMMIT_EDITMSG
.git/config
.git/description
.git/HEAD
.git/hooks
.git/hooks/applypatch-msg.sample
.git/hooks/commit-msg.sample
.git/hooks/post-update.sample
.git/hooks/pre-applypatch.sample
.git/hooks/pre-commit.sample
.git/hooks/pre-push.sample
.git/hooks/pre-rebase.sample
.git/hooks/pre-receive.sample
.git/hooks/prepare-commit-msg.sample
.git/hooks/update.sample
.git/index
.git/info
.git/info/exclude
.git/logs
.git/logs/HEAD
.git/logs/refs
.git/logs/refs/heads
.git/logs/refs/heads/master
.git/logs/refs/remotes
.git/logs/refs/remotes/origin
.git/logs/refs/remotes/origin/HEAD
.git/logs/refs/remotes/origin/master
.git/objects
.git/objects/04
.git/objects/04/1f29da84578ee14f4f5e5147a576d0580cea9d
.git/objects/info
.git/objects/pack
.git/objects/pack/pack-28fa62ca95b17883a7d6a1b6d9b2013a7d9ab751.idx
.git/objects/pack/pack-28fa62ca95b17883a7d6a1b6d9b2013a7d9ab751.pack
.git/packed-refs
.git/refs
.git/refs/heads
.git/refs/heads/master
.git/refs/remotes
.git/refs/remotes/origin
.git/refs/remotes/origin/HEAD
.git/refs/remotes/origin/master
.git/refs/tags
```