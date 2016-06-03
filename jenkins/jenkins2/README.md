# jenkins 2.0

### 課程難度：進階

Jenkins 2.0 版現在已經發佈。該版本增加了一種新的定義構建流程的方式，改善了新用戶的體驗。

Jenkins workflow plugin 並不是什麼新東西，但是2.0版本將提供一種新的核心特性（名字就叫 Pipeline），該特性允許用戶在 DSL（Domain Specific Language）的幫助下定義他們的構建流程。DSL 是 Groovy 其中之一的特性，允許把「建構設定(build definitioin)」當作一般程式碼撰寫。因此，建構設定就不只是定義在 Jenkins 的 task，而是可以被版本控制。

其實在此之前，有一些其他 Plugin 用來解決同樣的問題，但是 Jenkins 的創建者 Kohsuke Kawaguchi 對 InfoQ 說 Pipeline 不只是一款 Plugin。

實際上 Pipeline 是由一系列 Plugin 組成的一種意義重大的子系統。關於 2.0 版，我們其中一部分想法是想讓用戶拋棄「從內核開始然後安裝插件」的心態。取而代之的是，當你拿到 Jenkins 2.0 版的時候，你就會得到我們認為能覆蓋 80% 使用場景的功能，其中有些來自內核，有些來自 Plugin。
把管道功能作為核心特性也是業界中其他同行的做法。

紐約市的一名軟體工程師 Jacques Chester 認為，在關注 Jenkins Pipeline 功能的開發者也應該瞭解一下 Concourse。在一次 InfoQ 的採訪中，Chester 說Jenkins 的 Pipeline Plugin 系統其實是為其固有缺陷上的 Patch。

該系統將「通過 Plugin 而實現 Concourse 從設計之初就具有的部分功能從而重塑 Jenkins。Concourse 的基因是可以對整合流程進行版本控制，用完即可丟棄的構建環境以及可以將任務計劃委派給工具而不是手動組裝」。

另外，2.0 版的「Getting Started」有了一種新的體驗，在安裝插件方面為用戶提供一些建議。

## 課程內容

此章節將介紹 Jenkins 2.0 的新特性，以及在前面章節關於 Docker 的應用進行整合，透過 Pipeline 進行 CI 建置。


### 資料來源

<http://www.infoq.com/cn/news/2016/04/jenkins-2-beta-pipeline-system>
