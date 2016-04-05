OSX or Windows install docker
=============================

安裝 docker-tools
-----------------

docker-tools: https://www.docker.com/toolbox

安裝 docker-tools 將會自動安裝 Docker，docker-machine，docker-compose

透過 docker-machine 建立 docker engine vm
-----------------------------------------

`docker-machine create -d virtualbox dev`

啟動 docker-machine
-------------------

```
docker-machine start dev
```

預期結果
--------

```
Starting VM...
Started machines may have new IP addresses. You may need to re-run the `docker-machine env` command.
```

透過 docker-machine 連結 docker engine vm
-----------------------------------------

執行下列指令完成連結

```
eval $(docker-machine env default)
```

啟動 bash 時自動連結 docker engine vm
-------------------------------------

執行下列指令將連結

```
eval $(docker-machine env default)
```

確認 docker 運作正常
--------------------

若要確認是否正常運行，可以執行下列指令：

```
docker ps
```

正常將出現

```
CONTAINER ID  IMAGE  COMMAND  CREATED  STATUS  PORTS  NAMES
```

若出現下列訊息

```
Get http:///var/run/docker.sock/v1.20/containers/json: dial unix /var/run/docker.sock: no such file or directory.
* Are you trying to connect to a TLS-enabled daemon without TLS?
* Is your docker daemon up and running?
```

就有可能需要執行 `$(docker-machine env default)` 來進行連接。

若再不行，請

1.	確定 Virtual Box 是否最新 ，5.0.x 以上
2.	刪除 Virtual Box 管理介面的 default VM
3.	重新執行 Docker Quickstart Terminal

因為是使用 VM 的關係，若網路斷斷續續也會造成 Docker 網路不穩定，所以若有網路連不上的情形可以再重啟 VM
