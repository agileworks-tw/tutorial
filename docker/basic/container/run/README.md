run Container
=============

Container run 有兩種方式

1.	run with image
2.	start stopped container

透過 image 啟動 Container
-------------------------

取得基本的 ubuntu:latest image

`docker pull ubuntu:latest`

run docker image
----------------

`docker run -d -it ubuntu`

運行 ubuntu image 後，透過 `-t` 讓 Container 保持運作中

`-d` 是個很重要的 option，表示為 Daemonized 也就是背景執行，如此我們就可以再 Container 運行時，在進行其他操作。

### 檢視運行中 Container 狀況

透過下列指令

`docker ps`

將看到下列輸出內容

```
➜  ~ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
8e9ed1a4d9ce        ubuntu              "/bin/bash"         2 minutes ago       Up 2 minutes                            fervent_goldstine
```

表示 docker 目前正在運行中。

啟動 stopped Container
----------------------

接續上面的結果，透過下面指令將 Container 停止

```
docker stop 8e9ed1a4d9ce
```

### 重新啟動 docker Container

`docker start 8e9ed1a4d9ce`

### 重新啟動 docker Container 並且進入

再一次停止

`docker stop 8e9ed1a4d9ce`

再次啟動 Container 加上 `-i`

`docker start -i 8e9ed1a4d9ce`

一旦需要針對停止中的 Container 進行後續操作時，將可以再次進入 container 進行後續處理。
