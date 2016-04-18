private Docker hub
==================

若有需要自行架設 private docker hub 可以參考下列網址

[docker/distribution](https://github.com/docker/distribution/blob/master/docs/deploying.md)

舊版 private hub 叫做 `registry` 新版更為 distribution，新舊之間的名詞也需要知道，在查相關資料時才知道要使用的關鍵字。

對 docker 而言架設一個 private hub 就是啟動一個 container，相關操作練習步驟如下。

啟動 private hub
----------------

`docker run -d -p 5000:5000 --restart=always --name registry registry:2`

從 public hub 取得 ubuntu image
-------------------------------

`docker pull ubuntu`

變更 ubuntu tag 為 private hub image
------------------------------------

`docker tag ubuntu localhost:5000/ubuntu`

將 image push 到 private hub
----------------------------

`docker push localhost:5000/ubuntu`

再次從 private hub pull image
-----------------------------

`docker pull localhost:5000/ubuntu`
