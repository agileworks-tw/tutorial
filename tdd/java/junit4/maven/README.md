# JUnit 4 與 Maven

若專案是用 Maven 作為建置工具，我們可以對 `pom.xml` 設置 `<dependency>` 來加入 `junit` 的 dependency

設定方式如下。

```
  <dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
  </dependency>
```

因為 maven 約定大於配置的特性，執行下列指令：

```
mvn test
```

預設將會執行位於 `src/test/java` 的所有 *.java 的 Test Case

參考 Maven 官方 [Standard Directory Layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html) 文件，有其他不同 path 的使用時機。

若要指定特定得 Class 進行測試，我們可以使用

`-Dtest=TestSamle`

來進行，假設我們只要執行單一 Class 完整指令如下

`mvn -Dtest=TestSamle test`

Maven 會去找對應得 Class Name 來進行測試，若有同名的情況下就需要再加上 Package

一旦測試完成，我們可以在 `target/surefire-reports` 找到測試 report 可以使用 Jenkins 進行報表輸出。
