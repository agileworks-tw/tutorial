# Github Fork

`git remote -v`

```
origin  https://github.com/your-username/forked-repository.git (fetch)
origin  https://github.com/your-username/forked-repository.git (push)
upstream    https://github.com/original-owner-username/original-repository.git (fetch)
upstream    https://github.com/original-owner-username/original-repository.git (push)
```

```
git fetch upstream
git checkout master
git merge upstream/master
```



### 使用情境

* 常發生在長期無人維護的專案，但你需要使用並修改。
* 你需要用某個專案當基底，開發出一條完全新的路線。

![](assets/home_page.png)

![](assets/forking.png)

![](assets/fork_done.png)
