# javascript: performance & Tip


介紹幾篇關於效能的文章：

* [提升 JavaScript 效能的技巧](http://www.icoding.co/2012/07/javascript-html-2)
* [給非 JavaScript 專家的小技巧](http://www.icoding.co/2012/09/javascript2-html)
* [JavaScript秘密花園](http://bonsaiden.github.com/JavaScript-Garden/zh/)
* [Efficient JavaScript](http://dev.opera.com/articles/view/efficient-javascript/)
* [Efficient JavaScript 中文](http://www.woiweb.net/efficient-javascript.html)

節錄幾個重要的觀念：

## 1. 了解變數 scope 以及初始化

可參考我的另外一篇文章：[javascript: about scope][1]

## 2. 避免寫與 HTML 混在一起(inline)的 JavaScript

* 錯誤示範：

		<button id="my_btn" onclick="doThis();">Submit</button>

	把 JavaScript 跟 HTML 混在一起這樣寫會導致 JavaScript 異常的難以維護。一個新的開發者或需要更長的時間來找出散亂在 HTML 中的 script 並且很難將整個功能的情境拼湊出來。

* 正確：

		<button id="my_btn" type="button">Submit</button>

		<!-- These scripts go before the </body> tag. --><script type="text/javascript" src="/s/init.js"></script><script type="text/javascript">// <![CDATA[
		initializePage();
		    // pretend that these functions are in /s/init.js
		    function initializePage() {
		        document.getElementById("my_btn")
		            .addEventListener("click", doThis);
		    }
		    function doThis(e) {
		        // do cool stuff here
		    }
		// ]]></script>

另外關於這兩個寫法更進一步的差異可參考我另外一篇文章：[Javascript: What Is This?](http://smlsun.com/blog/2013/01/31/javascript-what-is-this/)，裡面有對類似的範例解釋對 this 的不同。

## 3. 找到對的 Event 去做 binding

比如說表單的提送按鈕上 bind “click" 事件處理實際上不是真的要處理 click ，而是要處理表單送出的事件。那麼這時候你應該 bind 的應該是表單的 “submit"，因為 enter 也會引發表單送出。

## 4. 使用快速的 selectors

如果你只是處理很小部份的 DOM elements，那麼用什麼方法其實沒有那麼重要，隨便你要使用 querySelector 或是 querySelectorAll。但如果你要處理的 DOM element 個數很大的話，記得使用比較快的方式（通常是最老的那個方法）。建議使用 getElementById，所有的瀏覽器都支援而且是目前最快的方式。

如果你用 jQuery 的話，最好還是使用 IDs 或是 classes 可以得到比較好的效能。


## 5. 非必要的時候不要去動 document

這應該是關於最佳化 JavaScript 效能最重要的技巧：沒事不要去動 document ，除非你百分之百確定你必須這麼做。這通常是大量使用 JavaScript 的網站的瓶頸。

盡量嘗試把 elements 的 reference 記下來，避免下次還要重新 query document 一次。

如同一開始提到的 [javascript: about scope][1] 文章中有介紹到的範例。

## 6. 等值檢查與真值

JavaScript 除了有一般的等值運算元 (==, !=)之外還有必較嚴格的等值運算元 (===, !==)。 差異如下：

* “5″ == 5 but “5″ !== 5
* 0 == false but 0 !== false
* null == undefined but null !== undefined

換句話說，=== 與 != 在比較的時候不會作自動的真值推導以及型別轉換，必須在兩邊的原始型別相同並且值也相同的情況下才為真。

## 7. 資料存取方式

有四種存取資料的方式分別是：

* 數值或字串  (literal value)
* 變數
* 物件屬性
* 陣列

在這四種方式裡面，literal 與區域變數的存取效率都很好，兩者不相上下。而物件跟陣列的存取相對於前者，效能就差很多。

物件屬性的深度也會對效能有影響。深度越深的話就自然得會越滿慢。所以在資料結構的設計上要小心。

在資料存取的建議是：

* 如果有一個物件屬性或陣列元素會被用到超過一次，就用區域變數取代它。
* 盡量減低物件或是陣列存取的深度。

## 8. 迴圈

不要使用 for … in 跟 for each。各個 JS framework 提供的 each 也要少用。尤其是每一次 iteration 都要執行一次函式的方式盡量少用。

## 9. DOM

在第 4. 使用快速的 selectors 有提到過，類似觀念如下：

透過 document.getElementsByTagName之類的函式取得的 HTMLCollection 的存取都很慢。因為每一次的存取都會重新做一次 DOM query。所以要盡量避免在迴圈中存取 HTMLCollection。但這畢竟是不可能的，建議將 HTMLCollection 轉成陣列後再做處理。不過如果你用 jQuery 的話大概不用擔心這個問題。因為 jQuery  會把 selector query 出來的 collection 轉成陣列，因此大概不會有這個問題。

關於 DOM 的效能問題，還有一個是 ReFlow，幾乎所有跟 DOM 物件的操作都會引發 ReFlow，新增或是移除 DOM 物件，或是改變 CSS 屬性，甚至是讀取 DOM 物件屬性，都有可能引發 ReFlow。要解決這個問題，必須利用 DocumentFragment，這是一個類似 document 的物件，但是並不在實際的 DOM Tree 裡面，因此在這個 fragment 上做操作不會引發 ReFlow，之後只要將這個 fragment add 到 DOM，所有的 fragment children 都會被加入到實際的 DOM Tree 中。在你其實並不懂 JavaScript 一文中亦有提及一個好的 JavaScript 開發者必須瞭解如何透過 DocumentFragment 來有效率的新增或移除 DOM Nodes。

關於 DocumentFragment 的使用可以參考這篇 [使用DocumentFragment來加快DOM操作速度](http://fstoke.me/blog/?p=2487)，裡面有提到：

> 用Firefox實測，使用第二種DocumentFragment寫法，速度快了將近一倍


## 10. 避免使用 eval 或 Function 構造函數

### 為什麼不要使用eval

每次eval或Function構造函數作用於字符串表示的源代碼時，腳本引擎都需要將源代碼轉換成可執行代碼。這是很消耗資源的操作——通常比簡單的函數調用慢100倍以上。

eval函數效率特別低，由於事先無法知曉傳給eval的字符串中的內容，eval在其上下文中解釋要處理的代碼，也就是說編譯器無法優化上下文，因此只能有瀏覽器在運行時解釋代碼。這對性能影響很大。


### 重寫eval

eval不僅效率低下，而且絕大部分情況下完全沒有使用的必要。很多情況下使用eval是因為信息以字符串形式提供，開發者誤認為只有eval能使用此信息。下例是一個典型的錯誤：

function getProperty(oString) {
  var oReference;
  eval('oReference = test.prop.'+oString);
  return oReference;
}

下面的代碼執行完全相同的函數，但沒有使用eval：

function getProperty(oString) {
  return test.prop[oString];
}

### Function

用 Function 類直接創建函數的語法如下：

	var function_name = new function(arg1, arg2, ..., argN, function_body)

	var doAdd = new Function("iNum", "alert(iNum + 10)");

可以看到其定義的方式與 eval 很像，因此也有類似 eval 的問題，只是 Function 構造函數比 eval 略好，因為使用此代碼不會影響周圍代碼；但其速度仍很慢。



### 偽裝的eval

定時函數 setTimeout和setInterval都可以接受字符串作為它們的第一個參數。這個字符串總是在全局作用域中執行，這個特性絕對不要使用，因為它在內部使用了eval。

function foo ()  {
    //將會被調用
}

function bar ()  {
    function foo ()  {
        //不會被調用
    }
    setTimeout ( 'foo()' ,  1000 );
}
bar ();

由於eval在這種情況下不是被直接調用，因此傳遞到setTimeout的字符串會自全局作用域中執行；因此，上面的回調函數使用的不是定義在bar作用域中的局部變量foo。

建議不要在調用定時器函數時，為了向回調函數傳遞參數而使用字符串的形式，這麼寫的代碼明顯質量很差。

	function foo ( a , b , c )  {}

	//不要這樣做
	setTimeout ( 'foo(1,2, 3)' ,  1000 )

	//可以使用匿名函數完成相同功能
	setTimeout ( function ()  {
	    foo ( a , b , c );
	},  1000 )

當需要向回調函數傳遞參數時，可以創建一個匿名函數，如上例，在函數內執行真實的回調函數，如此一來可避免使用 eval。



### 安全問題

eval 也存在安全問題，因為它會執行任意傳給它的代碼，在代碼字符串未知或者是來自一個不信任的源時，絕對不要使用eval函數。

### 結論

在任何情況下我們都應該避免使用eval函數。99.9%使用eval的場景都有不使用 eval的解決方案，任何使用它的代碼都會在它的工作方式，性能和安全性方面受到質疑。如果一些情況 ​​必須使用到eval才能正常工作，首先它的設計會受到質疑，這不應該是首選的解決方案，一個更好的不使用eval的解決方案應該得到充分考慮並優先採用。

在Opera 9, Firefox, 和Internet Explorer 中後者比前者快95%，在Safari 中快85%。(注意此比較中不含函數本身調用時間。)

特別需要提醒一下：在將 json String 轉換為 json Object 的時候，有些文章會有類似範例使用 eval 進行轉換，應該避免使用

建議可使用下列 js lib: [JSON-js](https://github.com/douglascrockford/JSON-js)




## 11. 自動分號插入

儘管JavaScript有C的代碼風格，但是它不強制要求在代碼中使用分號，實際上可以省略它們。

JavaScript不是一個沒有分號的語言，恰恰相反上它需要分號來就解析源代碼。因此JavaScript解析器在遇到由於缺少分號導致的解析錯誤時，會自動在源代碼中插入分號。

自動的分號插入被認為是JavaScript語言最大的設計缺陷之一，因為它能改變代碼的行為。

### 運作原理

下面的代碼沒有分號，因此解析器需要自己判斷需要在哪些地方插入分號。

	( function ( window ,  undefined )  {
	    function test ( options )  {
	        log ( 'testing!' )

	        ( options . list ||  []). forEach ( function ( i )  {

	        })

	        options . value . test (
	            'long string to pass here' ,
	            'and another long string to pass'
	        )

	        return
	        {
	            foo :  function ()  {}
	        }
	    }
	    window . test = test

	})( window )

	( function ( window )  {
	    window . someLibrary =  {}
	})( window )

下面是解析器"猜測"的結果。

	( function ( window ,  undefined )  {
	    function test ( options )  {

	        //沒有插入分號，兩行被合併為一行
	        log ( 'testing!' )( options . list ||  []). forEach ( function ( i )  {

	        });  // <-插入分號

	        options . value . test (
	            'long string to pass here' ,
	            'and another long string to pass'
	        );  // <-插入分號

	        return ;  // <-插入分號,改變了return表達式的行為
	        {  //作為一個代碼段處理
	            foo :  function ()  {}  
	        };  // <-插入分號
	    }
	    window . test = test ;  // <-插入分號

	//兩行又被合併了
	})( window )( function ( window )  {
	    window . someLibrary =  {};  // <-插入分號
	})( window );  //<-插入分號


建議絕對不要省略分號，同時也提倡將花括號和相應的表達式放在一行，對於只有一行代碼的if或者else表達式，也不應該省略花括號。這些良好的編程習慣不僅可以提到代碼的一致性，而且可以防止解析器改變代碼行為的錯誤處理，雖然 javascript 沒有強制檢查，但好的習慣可以避免不必要的麻煩。


## 12. 不要在影響性能的關鍵函數中使用try-catch-finally

try-catch-finally 結構比較特殊。和其他語法結構不同，它在 runtime 的當前作用域中創建新變量。每當catch執行時，就會將捕獲到的 exception 對象賦給一個變量。這個變量不屬於任何腳本。它在 catch 語句開始時被創建，在結束時被銷毀。

由於此函數比較特殊，且是在運行時動態創建動態銷毀，有些瀏覽器對其的處理並不高效。把catch 語句放在關鍵循環中將極大影響性能。

如果可能，應在腳本中不頻繁被調用的地方進行異常處理，或通過檢查某種動作是否被支持來避免使用。下面的例子中，如果所需的屬性不存在，將在循環語句中拋出許多異常：

	var oProperties = ['first','second','third',...,'nth'], i;
	for( i = 0; i < oProperties.length; i++ ) {
	  try {
	    test[oProperties[i]].someproperty = somevalue;
	  } catch(e) {
	    ...
	  }
	}


很多情況下，可把 try-catch-finally 結構移到循環外部。這樣做稍微改變了程序語義 ​​，因為如果拋出異常，將停止整個循環：
有時可用屬性檢測或其他檢測代替 try-catch-finally 結構：

	var oProperties = ['first','second','third',...,'nth'], i;
	try {
	  for( i = 0; i < oProperties.length; i++ ) {
	    test[oProperties[i]].someproperty = somevalue;
	  }
	} catch(e) {
	  ...
	}

## 13. location.replace()控制歷史項

有時需要通過腳本修改頁面地址。常見的方法是給location.href賦新地址。這將和打開新鏈接一樣添加新歷史項、載入新頁面。
有時不想添加新歷史項，因為用戶不需要回到前面的頁面。這在內存資源有限的設備中很有用。通過替換歷史項恢復當前頁面所使用的內存。可以通過location.replace()方法實現。

注意頁面仍被保存在cache 中，仍佔用內存，但比保存在歷史中要少的多。

[1]: http://smlsun.com/blog/2013/02/01/javascript-about-scope/
