# test

延續 task/[build](./build.md)

我們可以建置透過 build task 直接複製如下圖：

![](../images/test/addTestTask.png)

## 建置指令

```
#!/bin/bash
mvn clean cobertura:cobertura test
```

## 設置 JUnit 呈現測試報告

設置 task output report
-----------------------

![](images/test-report/post-select.png)

設定讀取 report 位置
--------------------

![](images/test-report/task-setting.png)

如上圖所示，將 Test report XMLs 設置為 `target/surefire-reports/*.xml`

檢視 test report
----------------

![](images/test-report/report.png)


## 設置 Cobertura 呈現測試覆蓋率報告

report 位置：`target/site/cobertura/coverage.xml`

### 執行結果

![](images/testResult.png)
