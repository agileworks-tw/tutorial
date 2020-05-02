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
上述關於 /dev/null 2>&1 的解釋：

1. 系統將標準輸入/輸出分成三個，分別是 stdin (fd 是 0)，stdout (fd 是 1)，及 stderr (fd 是 2)，在這裡 2 代表標準錯誤輸出 stderr。
2. &: 設定使用 fd 代號, 如果 `> dev/null 2>&1` 沒有加上 `&`，會視後面的 `1` 為檔案名稱, 而不是 fd。

“> /dev/null 2>&1” 的完整解釋：將左邊程式的所有標準輸出 stdout，及標準錯誤輸出 stderr 導向到 /dev/null，即左邊的程式只會執行，而不會輸出任何程式執行的結果。

來源：<https://www.opencli.com/linux/dev-null-2-and-1-meanning>

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
