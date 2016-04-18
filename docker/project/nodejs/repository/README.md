範例專案以 Node.js 為例
-----------------------

範例 github repository
----------------------

[https://github.com/TrunkWorkshop/sailsSample](https://github.com/TrunkWorkshop/sailsSample)

clone repository
----------------

透過下面指令，將會複製飯粒專案

`git clone https://github.com/TrunkWorkshop/sailsSample.git`

建置專案
--------

透過下列指令將會把 package.json 中定義的套件進行安裝

```
npm install
npm build
```

測試專案
--------

透過下列指令，將會運行自動測試。

`npm test`

運行專案
--------

透過下列指令，將會運行 development mode 作為開發中方確認結果。

`npm start`

透過下列網址

`http://localhost:1337/`

可以存取範例專案運行結果

打包專案
--------

```
npm run build-prod
zip -r build.zip ./
```

production run
--------------

```
npm run build-prod
npm run start-prod
```

透過下列網址

`http://localhost:1337/`

可以存取 production mode 範例專案運行結果。
