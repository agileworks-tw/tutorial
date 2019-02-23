# 版本版號資訊寫入資訊

Jenkins 建置時每次建置都會有對應的環境變數，參考下面連結

https://wiki.jenkins.io/display/JENKINS/Building+a+software+project#Buildingasoftwareproject-below

相關資訊只要透過 Jenkins 進行專案建制，就可以作為專案版本資訊的依據。

此章節將說明如何應用該功能，讓專案打包後進行發布時，可以取得對應的版本資訊

## 設置 maven 

在 pom.xml 我們可以定義所需的參數，如下：

```
	<version>${revision}</version>
    <properties>
        <buildNumber>local</buildNumber>
        <revision>1.0.0+${buildNumber}</revision>
    </properties>

```

其中 properties 底下的參數值，都可以透過下面指令進行替換

`mvn clean package -DbuildNumber=b01`

如此我們就可以在建置時帶入 Jenkins 建制時的環境變數。

以上面的例子，執行指令之後，我們可以得到產出的檔案名稱為

`spring-boot-sample-data-rest-1.0.0+b01.jar`

接著若我們要讓版號資訊能夠在程式運作時能夠查詢到，我們可以把相關資訊寫入專案運作時可讀取的到的設定檔

參考此連結說明

https://maven.apache.org/plugins/maven-resources-plugin/examples/filter.html

我們可以接著在 POM.xml 加入下面設置

```
      ...
      <resource>
        <directory>src/main/resources</directory>
        <filtering>true</filtering>
      </resource>
      ...
```

這樣設置後，maven 在執行 command 時，會去掃描底下的檔案，只要有對應的 properties 之 key 值就會被替換，如：

`info.app.version=@revision@`

用 `@propertiesKeyName@` 作為替需要參數帶入的表示方式，只要確保相關設定檔版本相關資訊正確寫入，就可以在軟體運作時讀取並呈現相關資訊。



