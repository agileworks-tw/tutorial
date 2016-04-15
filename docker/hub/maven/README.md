maven
=====

作為 java 的主要主要的專案管理與自動化編譯工具，也是在寫 java 程式時不可或缺的，以往我們因為不同 java 版本搭配不同 maven 都需要額外安裝，現在透過 docker 可以很方便進行切換，相關版本有：

-	3.3.9-jdk-7, 3.3-jdk-7, 3-jdk-7 (jdk-7/Dockerfile)
-	3.3.9-jdk-7-onbuild, 3.3-jdk-7-onbuild, 3-jdk-7-onbuild (jdk-7/onbuild/Dockerfile)
-	3.3.9-jdk-8, 3.3.9, 3.3-jdk-8, 3.3, 3-jdk-8, 3, latest (jdk-8/Dockerfile)
-	3.3.9-jdk-8-onbuild, 3.3.9-onbuild, 3.3-jdk-8-onbuild, 3.3-onbuild, 3-jdk-8-onbuild, 3-onbuild, * onbuild (jdk-8/onbuild/Dockerfile)
-	3.3.9-jdk-9, 3.3-jdk-9, 3-jdk-9 (jdk-9/Dockerfile)
-	3.3.9-jdk-9-onbuild, 3.3-jdk-9-onbuild, 3-jdk-9-onbuild (jdk-9/onbuild/Dockerfile)
-	3.3.3-jdk-7 (jdk-7/Dockerfile)
-	3.3.3-jdk-7-onbuild (jdk-7/onbuild/Dockerfile)
-	3.3.3-jdk-8, 3.3.3 (jdk-8/Dockerfile)
-	3.3.3-jdk-8-onbuild, 3.3.3-onbuild (jdk-8/onbuild/Dockerfile)
-	3.3.3-jdk-9 (jdk-9/Dockerfile)
-	3.3.3-jdk-9-onbuild (jdk-9/onbuild/Dockerfile)

執行範例如下：

```
docker run -it --rm \
--name my-maven-project \
-v "$PWD":/usr/src/mymaven \
-w /usr/src/mymaven \
maven:3.2-jdk-7 \
mvn -v
```

透過 `-v` 可以把要搭配 maven 進行專案建置的原始碼掛載到 maven docker 內，如此就可以進行建置工作。

若要確認 maven 版本是否正確，可以使用下列指令

```
docker run -it --rm \
--name my-maven-project \
maven:3.2-jdk-7 \
mvn -v
```

執行完將會看到下列訊息

```
Apache Maven 3.2.5 (12a6b3acb947671f09b81f49094c53f426d8cea1; 2014-12-14T17:29:23+00:00)
Maven home: /usr/share/maven
Java version: 1.7.0_75, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-7-openjdk-amd64/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "4.1.19-boot2docker", arch: "amd64", family: "unix"
```
