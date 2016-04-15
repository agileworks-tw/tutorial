mysql
=====

作為 database，mysql 是很常用的一個 solution，docker 官方就有提供 mysql 的 image，目前提供的版本有：

-	5.5.48, 5.5 (5.5/Dockerfile)
-	5.6.29, 5.6 (5.6/Dockerfile)
-	5.7.11, 5.7, 5, latest (5.7/Dockerfile)

若要使用可以參考下列指令：

```
docker run -d \
-e MYSQL_ROOT_PASSWORD=root \
-p 3306:3306
-v $HOME/datadir:/var/lib/mysql
mysql
```

其中

-	`-p`: 把 3306 port 開放將可以透過 mysql client 進行 mysql server 的存取。
-	`-v`: 把 `/var/lib/mysql` 掛載到 host 之檔案系統將可以持久化資料。
