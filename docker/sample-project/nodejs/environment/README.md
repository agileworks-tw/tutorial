Node.js 開發環境安裝
====================

安裝 nvm
--------

透過 nvm 來進行 NodeJS 安裝，指令如下：

```
touch ~/.bashrc
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```

安裝完之後會在 user 的 `~/.bashrc` 寫入下列指令

```
export NVM_DIR="/var/lib/jenkins/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
```

這段最主要的用意就是要把 nvm 載入，之所以需要寫入 `~/.bashrc` 就是要在登入時將 nvm 載入。

驗證 nvm 以安裝完成
-------------------

透過 `nvm --version` 確認已確實載入完成

安裝 Node.js
------------

`nvm install v4`

透過 nvm 的協助我們可以很方便進行 NodeJS 版本切換，這也會使我們在建置時可以很方便的切換版本。

如果你要設置某個版本為預設，可以使用下列指令

`nvm alias default v4`

如此我們可以確認一下目前 NodeJS 的版本

`node -v`

pm2: global 套件安裝
--------------------

pm2 作為 Node.js 運行為 daemon 模式所開發的套件，我們可以事先安裝

```
npm i pm2 -g
```
