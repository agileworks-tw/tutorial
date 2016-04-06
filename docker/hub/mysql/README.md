mysql
=====

作為 database，mysql 是很常用的一個 solution，docker 官方就有提供 mysql 的 image

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
