ubuntu
======

ubuntu 作為最常用的 linux distribution 常拿來作為 base OS，很多範例也是用 ubuntu 作為基底，目前為止，有的版本為

-	12.04.5, 12.04, precise-20160330, precise (precise/Dockerfile)
-	14.04.4, 14.04, trusty-20160405, trusty, latest (trusty/Dockerfile)
-	15.10, wily-20160329, wily (wily/Dockerfile)
-	16.04, xenial-20160331.1, xenial (xenial/Dockerfile)

最常用的 docker run 指令為

`docker run -it ubuntu`

完整指令其實為

`docker run -it ubuntu /bin/bash`

也就是登入 bash，接著就可以進行相關的套件安裝。
