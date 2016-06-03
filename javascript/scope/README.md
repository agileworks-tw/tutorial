# scope

#### 參考來源

* [提升 JavaScript 效能的技巧](http://www.icoding.co/2012/07/javascript-html-2)
* [給非 JavaScript 專家的小技巧](http://www.icoding.co/2012/09/javascript2-html)

這篇文章是根據上面文章，整理與 scope 相關的資料彙總而成。


scope 的產生與函式息息相關，首先必須先了解函式的運作

## 函式是如何被初始化

1. 先宣告函式參數，並設定參數的值
2. 所有函式內部的函式被宣告
3. 所有在這函式 scope 中有宣告的變數被生成 (所以即使變數被宣告在最後一行，但卻可已在函式中的任何地方被存取)
4. 賦予變數值

接著來看 scope

## 了解變數 scope 以及初始化

1. 唯一的變數 scope 就是你所在的函式。
2. 還有全域的 scope，但並沒有區塊的 scope。
3. 每一個函式都有一個 scope chain，而這個 chain 中會指向上一層函式的 scope。
4. 如果一個變數或是函式被存取但是在當下的 scope 中找不到，這時候就會嘗試往上一層的 scope 去找一直到有一個對應個宣告被找到為止。
5.  如果是嘗試賦予一個變數的值，但往上找卻找不到對應宣告的時候，那麼就會直接在全域 scope 設定一個這個變數名字的屬性。

## scope 的運作原理

當你定義一個全域函式的時候，那根據 ECMAScript 規格，它就會有一個 [[Scope]]屬性，而這個 [[Scope]] 會指到一個 Scope Chain Table，這個 table 裡面存放一個指到 global variables 的 table。


![img](http://2.bp.blogspot.com/-gugDSqh-lUg/T_XMYmUT5fI/AAAAAAAAXUE/WqDmooAtSwM/s1600/scope.jpeg)


之後，當一個函式被執行的時候，對應的 execution context 會被生成，而這個 execution context 會有一個屬於自己的 scope chain，這個 scope chain 會被用來作變數解析。

這個 execution context 一開始先把函式的 [[scope]] 複製一份，之後再產生一個 activation object 裡面指到所有的 local variables table，並把這個 activation object 放在 scope chain 的一開始，所以當 setup 被執行的時候 scope chain 應該是長這樣：

![img](http://1.bp.blogspot.com/-3MdmGetL9rE/T_XMhQIwBhI/AAAAAAAAXUY/6I2Ota50G6o/s1600/scope2.jpeg)

當在 function scope 裡面做任何變數的存取的時候，第一步就是先從位於 0 的 scope chain 開始找，如果沒找到就會再往下一個位置去找。

這也是一般大家理解的會先取用 local 的，之後再往上一層，最後一直都找不到的話，就會產生錯誤。

這邊的重點就是 global 的變數永遠都會在 scope chain 的最後面那一層，所以盡可能地使用 local variables，因為這總是比 global variables快，也就是 jQuery 原始碼裡面將 window 轉換成 local 所提到的效能問題是一樣的。

接著必須了解scope management的知識，對於效能改善是很重要的。

## scope management

關於 scope management，還有一點很重要的，常聽到人家說不要用 with，而 scope 是其中的一個原因。當你用了 with 的時候其實是在 scope chain 裡面硬加了一個暫時的 scope 在最前面的地方，當離開 with scope 的時候，這個 with scope 物件就消失。

所以在 with 的範圍內，所有原本的 local variables 的存取都變慢了。另外，try/catch 也一樣有這個問題。

在 closure 的部分，可以想像的是至少會有三個 scope chain，一個是 global，一個是 containing function 的 activation context，還有一個是最前面的 local。可以想見 closure 的使用也會影響資料存取的效能，因為存取階層變多的關係。

## 效能改善相關

1. 對那些常常會存取的變數，盡量把它放在 local
2. 避免使用 with
3. 小心使用 try / catch

	> 至於為什麼可以參考 [Javascript: Performance](http://smlsun.com/blog/2013/02/01/javascript-performance/) 中的第 12. 不要在影響性能的關鍵函數中使用try-catch-finally 說明

4. 沒有必要的話不要用 closure
5. 不要忘記在宣告變數時要加上 var，不然你會不小心宣告太多全域變數

根據以上原則，範例函式如下，使用全域函式 setup，也就是 ``document``。：

``` javascript
  function setup(items)
  {
      var divs = document.getElementsByTagName("div");
      var images = document.getElementsByTagName("image");
      var button = document.getElementsById("save-btn");

      for (var i = 0; i < items.length; i++) {
          process(items[i], div[i]);
      }

      button.addEventListener("click", function(event) {
          alert("Saved");
      }, false);
  }
```

應該要先將 ``document`` 指定給區域變數，修正如下：

``` javascript

  function setup(items)
  {
      var doc = document; // 原本沒有這行

      // document 全部替換為 doc，也就是改為區域變數
      var divs = doc.getElementsByTagName("div");
      var images = doc.getElementsByTagName("image");
      var button = doc.getElementsById("save-btn");

      for (var i = 0; i < items.length; i++) {
          process(items[i], div[i]);
      }

      button.addEventListener("click", function(event) {
          alert("Saved");
      }, false);
  }
```
