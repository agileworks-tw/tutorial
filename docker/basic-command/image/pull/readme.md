docker image 操作
=================

一開始使用 docker 時，可以從 docker hub 取得已經存在的 docker image，可以透過

`docker pull`

來進行。

我們可以從最常用的 ubuntu 作為此章節的練習

pull ubuntu
-----------

執行下面指令

`docker pull ubuntu`

終端機將會出現下面訊息

```
➜  ~ docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu

d38575f188e0: Pull complete
b04ea90f261c: Pull complete
40dc9cd44ffa: Pull complete
a3ed95caeb02: Pull complete
Digest: sha256:4bc45eecd925cb8806294d0e8bc5c1cfd1149c6dd8a5ef2165b6c02eabb8821f
Status: Downloaded newer image for ubuntu:latest
```

該命令實際上相當於

`docker pull registry.hub.docker.com/ubuntu`

即從註冊服務器 `registry.hub.docker.com` 取得其中的 ubuntu image。

若有自行架設 docker hub 的需求，就可以透過更改網址的方式來指定下載 image 的位置

若有需要自行架設 private docker hub 可以參考下列網址

[docker/distribution](https://github.com/docker/distribution/blob/master/docs/deploying.md)
