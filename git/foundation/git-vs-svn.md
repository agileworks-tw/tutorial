# Git VS SVN

### Git

* Straight merge 預設的合併模式，會有全部的被合併的 branch commits 記錄加上一個 merge-commit，看線圖會有兩條 Parents 線，並保留所有 commit log。


### SVN

* Squashed commit 壓縮成只有一個 merge-commit，不會有被合併的 log。


### transport

![Git transport](https://patrickzahnd.ch/uploads/git-transport-v1-1024x723.png)

![SVN transport](https://patrickzahnd.ch/uploads/svn-transport-v1.png)


### 比較

* Git 的「送交」與「發布」步驟是分開的
* Git 沒有唯一的真實歷史紀錄，在分散式開發環境中，大家都是平等的。
* 時間戳不重要，重點是「父子關係」。