exec Container
==============

exec 指令主要使用時機為一旦 docker Container 運行時，當你需要除錯希望再次進入 Container，或是希望對 Container 內執行相關指令時提供給使用者再次執行指令的機會。

取得基本的 ubuntu:latest image
------------------------------

`docker pull ubuntu:latest`

run docker image
----------------

`docker run -d -it ubuntu`

如此 docker Container ubuntu 將在背景中執行

檢視運行中 Container 狀況
-------------------------

透過下列指令

`docker ps`

將看到下列輸出內容

```
➜  ~ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
8e9ed1a4d9ce        ubuntu              "/bin/bash"         2 minutes ago       Up 2 minutes                            fervent_goldstine
```

再次進入運行中的 Container
--------------------------

```
docker exec -t 8e9ed1a4d9ce /bin/bash
```
