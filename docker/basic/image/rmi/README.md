移除 image
==========

若要移除 image 我們可以使用 `rmi` 指令，需要注意的是，在執行之前要確保所有相關的 Container 必須要移除

首先取出 ubuntu image

```
docker pull ubuntu
```

執行刪除 image
--------------

`docker rmi ubuntu:latest`

強制執行刪除 image
------------------

若確定運行 Container 中已不需要，可加上 `-f` 強制刪除 image

`docker rmi -f ubuntu:latest`
