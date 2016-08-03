# JUnit 4 與 Maven

Maven 是被廣泛使用的 Java 專案建置工具（Build tools），這個單元我們使用 Maven 來建置與測試 Java 範例專案。

## Maven Surefire Plugin

Maven 負責執行測試的 Plugin 名為 `maven-surefire-plugin`，它預設會使用 JUnit 測試框架，但不侷限於 JUnit，你也可以使用其他常見 Java 測試框架如 TestNG 等。

參考 maven-surefire-plugin 網頁：

http://maven.apache.org/plugins/maven-surefire-plugin/

## Git Repository

取得範例程式碼：

```
git clone https://github.com/agileworks-tw/junit4-samples.git
```

## File Structure

依循 Maven 的 [Standard Directory Layout](https://goo.gl/7F8xaJ) 放置相關程式檔案。

* `src/main/java`         <br/> Application/Library sources
* `src/main/resources`    <br/> Application/Library resources
* `src/test/java`         <br/> Test sources
* `src/test/resources`    <br/> Test resources

此範例位於 `maven/` 資料夾，主要的檔案包括：

* `pom.xml`                             <br/> Maven 設定
* `src/main/java/Calculator.java`       <br/> 主程式
* `src/test/java/CalculatorTest.java`   <br/> 測試

## Maven POM

`pom.xml` 是 Maven 主要的設定檔，只需要在 `<dependency>` 加入 JUnit 相關設置，即可讓 Maven 進行測試。

File Name: `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.mycompany.app</groupId>
  <artifactId>my-app</artifactId>
  <packaging>jar</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>Maven Quick Start Archetype</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```

執行：

```
mvn test
```

## Running Tests in Parallel

運用多執行緒同時執行多個 Test 以加速測試執行。

```xml
  <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.19.1</version>
    <configuration>
      <parallel>methods</parallel>
      <threadCount>10</threadCount>
    </configuration>
  </plugin>
```
