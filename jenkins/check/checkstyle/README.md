# checkStyle

checkStyle 主要用於檢查 coding style 是否正確，透過 checkStyle 可以讓程式為我們的專案進行 Style 的把關

搭配 Warnings Next Generation plugin 使用，套件網址：

https://plugins.jenkins.io/warnings-ng

## maven POM.xml 設定

透過 maven POM.xml 定義，可以讓我們使用 mvn 指令來進行 checkStyle

```
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-checkstyle-plugin</artifactId>
  <version>2.9.1</version>
  <executions>
      <execution>
      <id>checkstyle</id>
      <phase>validate</phase>
      <goals>
          <goal>check</goal>
      </goals>
      <configuration>
          <failOnViolation>false</failOnViolation>
      </configuration>
      </execution>
  </executions>
</plugin>
```

執行 `mvn checkstyle:checkstyle` 來進行 checkstyle 的執行

可以在 `${project_home}/target/site/checkstyle.html` 檢視 report 的產出。

而用於 jenkins 產出 report 所需的 xml 檔案路徑為 `target/checkstyle-result.xml`

## 利用 Jenkins 產出 Report

![](assets/2019-02-22-14-41-41.png)

若 `Checkstyle results` 沒有設置的情況下，預設為 `**/checkstyle-result.xml`，設置畫面如下：

![](assets/2019-02-22-14-45-26.png)

產出報表畫面：

![](assets/2019-02-22-14-46-23.png)

![](assets/2019-02-22-14-46-41.png)

![](assets/2019-02-22-14-46-55.png)

![](assets/2019-02-22-14-47-17.png)

## 參考資料

<http://www.cnblogs.com/huang0925/p/3148389.html>
