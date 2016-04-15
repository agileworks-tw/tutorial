alpine
======

與 ubuntu 類似，常常作為 base OS 所使用，不一樣的是，此 image 的大小只有 5 mb，作為 docker 之 base image 非常的適合！有越來越多 docker image 使用 alpine 為基底，目前有的版本為。

-	3.1 (versions/library-3.1/Dockerfile)
-	3.2 (versions/library-3.2/Dockerfile)
-	3.3, latest (versions/library-3.3/Dockerfile)
-	edge (versions/library-edge/Dockerfile)

與 ubuntu 不一樣的是，安裝軟體時，ubuntu 是透過 `apt-get` 來進行，alpine 則是透過 `apk add` 來進行

以製作 node.js 之 docker 為例，其 Dockerfile 如下

```
FROM alpine:latest
RUN apk --update --no-progress add nodejs unrar bash git
WORKDIR /root
```

分別使用 ubuntu 以及 alpine 建置 node.js image 其檔案大小差異如下

```
dahlb/alpine-node             latest              f305b592c570        5 minutes ago       46.2 MB
node                          latest              86cbce15c689        7 days ago          644.3 MB
```

可以看到差距超過 10 倍。
