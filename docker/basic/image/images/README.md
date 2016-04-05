列出所有的 docker images
========================

透過下列指令

`docker images`

可以列出目前已經存的 docker images，執行結果如下

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
ubuntu                        latest              a1e4ed2ac65b        8 hours ago         188 MB
ubuntu                        14.04               07c86167cdc4        4 weeks ago         188 MB
```

其中

REPOSITORY
----------

來自哪個 image

TAG
---

版本標記，在 pull image 時若沒有給定 tag 預設為 latest

IMAGE ID
--------

image 的唯一識別編號，可作為運行時唯一識別用如下列指令

`docker run -it 07c86167cdc4 /bin/bash`

也等同於

`docker run -it ubuntu:14.04 /bin/bash`
