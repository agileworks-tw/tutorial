Node,js
=======

官方提供的 Node.js 版本如下

-	0.10.44, 0.10 (0.10/Dockerfile)
-	0.10.44-onbuild, 0.10-onbuild (0.10/onbuild/Dockerfile)
-	0.10.44-slim, 0.10-slim (0.10/slim/Dockerfile)
-	0.10.44-wheezy, 0.10-wheezy (0.10/wheezy/Dockerfile)
-	0.12.13, 0.12, 0 (0.12/Dockerfile)
-	0.12.13-onbuild, 0.12-onbuild, 0-onbuild (0.12/onbuild/Dockerfile)
-	0.12.13-slim, 0.12-slim, 0-slim (0.12/slim/Dockerfile)
-	0.12.13-wheezy, 0.12-wheezy, 0-wheezy (0.12/wheezy/Dockerfile)
-	4.4.3, 4.4, 4, argon (4.4/Dockerfile)
-	4.4.3-onbuild, 4.4-onbuild, 4-onbuild, argon-onbuild (4.4/onbuild/Dockerfile)
-	4.4.3-slim, 4.4-slim, 4-slim, argon-slim (4.4/slim/Dockerfile)
-	4.4.3-wheezy, 4.4-wheezy, 4-wheezy, argon-wheezy (4.4/wheezy/Dockerfile)
-	5.10.1, 5.10, 5, latest (5.10/Dockerfile)
-	5.10.1-onbuild, 5.10-onbuild, 5-onbuild, onbuild (5.10/onbuild/Dockerfile)
-	5.10.1-slim, 5.10-slim, 5-slim, slim (5.10/slim/Dockerfile)
-	5.10.1-wheezy, 5.10-wheezy, 5-wheezy, wheezy (5.10/wheezy/Dockerfile)

執行範例如下：

```
docker run -it --rm \
--name my-running-script \
-v "$PWD":/usr/src/app \
-w /usr/src/app node:4 \
node your-daemon-or-script.js
```

透過 `-v` 可以把要搭配 Node.js 進行專案建置的原始碼掛載到 Node.js docker 內，如此就可以進行建置工作。

若要確認 Node.js 版本是否正確，可以使用下列指令

```
docker run -it --rm \
--name my-running-script \
node node -v
```

執行完將會看到下列訊息

```
v5.9.0
```
