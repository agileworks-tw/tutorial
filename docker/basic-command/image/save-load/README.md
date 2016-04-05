save 及 load image
==================

如果因為網路限制需要透過離線的方式安裝 image 時將會需要使用。

首先取出 ubuntu image

```
docker pull ubuntu
```

save docker image
-----------------

`docker save -o ubuntu_latest.tar ubuntu:latest`

load docker image
-----------------

`docker load --i ubuntu_latest.tar`
