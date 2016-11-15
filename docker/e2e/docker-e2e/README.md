# 透過 Docker 運行專案並執行 e2e test

### docker-compose

```
debug:
  container_name: debug
  image: agileworks/sails_sample_env
  command: "/bin/sh"

  expose:
    - "1338"
  ports:
    - "5001:5001"

  volumes:
    - ./:/sailsSample
  working_dir: /sailsSample

  depends_on:
    - "e2e-env"

  networks:
    - front-tier
```

```
e2e-env:
  container_name: e2e-env
  image: selenium/standalone-firefox-debug:2.53.0
  expose:
    - "4444"
  ports:
    - "5900:5900"
  networks:
    - front-tier
```

可以看到在 debug 的 service 定義了

```
expose:
  - "1338"
networks:
  - front-tier
```

而 e2e-env 的 service 定義為

```
expose:
  - "4444"
networks:
  - front-tier
```

兩個 Container 在 networks 定義了同樣的 `front-tier`，代表兩個 Container 可以互通。

因為兩個 Container 存在於同一個 network 我們就可以透過 `container_name` 直接作為 hostname 進行存取。

而 `expose` 則定義可以透過哪個連接阜進行存取。

如若要在 `e2e-env` container 存取 `debug` container 啟動的 server 我們可以使用

`http://debug:1338` 來瀏覽專案的網頁，也就可以作為前端測試使用。

其中專案已設置若 `environment` 為 `test`，則 `port` 會使用 `1338`

根據上面的設定我們需要有另外一個設定檔告訴 `web-driver` 測試 server 及測試瀏覽器如何進行互動測試。

## 前端測試設定檔

檔案位置 `chimp-docker.js`

```
module.exports = {
  port: 4444,
  host: "e2e-env",
  browser: 'firefox',
  webdriverio: {
    baseUrl: 'http://debug:1338',
  }
};
```

上面的設定檔與 `docker-compose` 設定對應

```
port: 4444,
host: "e2e-env",
```

告訴測試框架透過上面的 `port` 及 `host` 控制 browser

而下面則設定要測試的標的，也同樣跟 `docker-compose` 呼應

```
webdriverio: {
  baseUrl: 'http://debug:1338',
}
```

## 運行前端測試

`npm run test-e2e-docker`

## 前端測試除錯

`vnc://localhost:5900`
