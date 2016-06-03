preview
=======

建置指令
--------

參考 task/[build](buld.md)

透過 ssh 進行 preview
---------------------

### ssh publish setup

-	Name: 選擇在 [publish-over-ssh](../plugin/publish-over-ssh.md) 建置的 ssh server
-	Source files: target/spring-boot-sample-data-rest-0.1.0.jar
-	Remote directory: deploy/preview

### preview 執行指令

```
cd deploy/preview

kill `cat run.pid` || true
kill `cat ../release/run.pid` || true

java -jar target/spring-boot-sample-data-rest-0.1.0.jar > /dev/null 2>&1 & echo $! > run.pid
```

如此就可以很快速的將最新的程式碼啟動進行功能驗證

> 之所以這樣處理，因為 preview 跟 production release 非常像，下一個章節將可以直接複製修正
