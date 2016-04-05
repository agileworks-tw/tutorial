remove container
================

首先啟動一 container

`docker run ubuntu`

因為沒有加上任何 option，執行後隨即停止

可以透過

`docker ps -a`

查出所有 Container 包括已停止的，輸出如下

```
➜  ~ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
270ea7ee8b06        ubuntu              "/bin/bash"         5 seconds ago       Exited (0) 4 seconds ago                       boring_panini
```

刪除 stopped container
----------------------

`docker rm 270ea7ee8b06`

強制刪除運行中 Container
------------------------

`docker rm -f 270ea7ee8b06`
