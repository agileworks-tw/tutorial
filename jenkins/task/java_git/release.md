部署
==========

## release 指令使用 Makefile

```
deploy-default:
	ssh jenkins@localhost mkdir -p deploy/release
	scp target/spring-boot-sample-data-rest-0.1.0.jar jenkins@localhost:deploy/release
	- ssh jenkins@localhost 'kill `cat deploy/release/run.pid`'
	ssh jenkins@localhost 'java -jar deploy/release/spring-boot-sample-data-rest-0.1.0.jar > /dev/null 2>&1 & echo $$! > "deploy/release/run.pid"'

```

幾個重點如下：

```
- ssh jenkins@localhost 'kill `cat deploy/release/run.pid`'
```

上述指令開頭的 `-` 表示該指令執行失敗不影響最後結果。

`/dev/null 2>&1 & echo $$! >` 其中 `$$` 若在 terminal 執行只需要一個 `$` 因為 `$` 在 makefile 中為特殊字元，透過 `$$` 來進行跳脫，若在 terminal 執行，完整指令如下

`ssh jenkins@localhost 'java -jar deploy/release/spring-boot-sample-data-rest-0.1.0.jar > /dev/null 2>&1 & echo $! > "deploy/release/run.pid"'`

## jenkins release bash shell

實際在 jenkins 中的 bash shell 只需要執行下面指令

```
make deploy-default
```

即可完成上述多行指令的執行
