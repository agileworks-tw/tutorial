# callback

#### 資料來源

[JavaScript callback function 理解](http://mao.li/javascript/javascript-callback-function/)


## 定義


* 維基的Callback_(computer_programming):

	>In computer programming, a callback is a reference to a piece of executable code that is passed as an argument to other code.

* jQuery文檔How jQuery Works#Callback_and_Functio…：

	>A callback is a function that is passed as an argument to another function and is **executed after its parent function has completed**. The special thing about a callback is that functions that appear after the "parent" can execute before the callback executes. Another important thing to know is how to properly pass the callback. This is where I have often forgotten the proper syntax.

* 百科： callback 函數

	>callback 函數就是一個通過函數指針調用的函數。如果你把函數的指針（地址）作為參數傳遞給另一個函數，當這個指針被用為調用它所指向的函數時，我們就說這是 callback 函數。

	>callback 函數不是由該函數的實現方直接調用，而是在特定的事件或條件發生時由另外的一方調用的，用於對該事件或條件進行響應。

因此， callback 本質上是一種設計模式，並且jQuery(包括其他框架)的設計原則遵循了這個模式。

在JavaScript中，callback 函數具體的定義為：函數A作為參數(函數引用)傳遞到另一個函數B中，並且這個函數B執行函數A。我們就說函數A叫做 callback 函數。如果沒有名稱(函數表達式)，就叫做匿名 callback 函數。

因此 callback 不一定用於非同步的狀況，一般同步(blocking)的場景下也經常用到 callback ，比如要求執行某些操作後執行 callback 函數。

## 範例

一個同步(blocking)中使用 callback 的例子，目的是在func1代碼執行完成後執行func2。

``` javascript
	var func1=function(callback){
	    //do something.
	    (callback && typeof(callback) === "function") && callback();
	}

	func1(func2);

	var func2=function(){
		alert("func2 run!");
	}
```

非同步 callback 的例子：

``` javascript
	$(document).ready(callback);

	$.ajax({
	  url: "test.html",
	  context: document.body
	})
	.done(function() {
	  $(this).addClass("done");
	})
	.fail(function() { alert("error");
	})
	.always(function() { alert("complete");
	});
```

上述例子為非同步 ajax 請求，當request 有 response 時,如果先前已定義 callback ,將會觸動相關的函數進行執行。

## callback 什麼時候執行

 callback 函數，一般在同步情境下是最後執行的，而在非同步情境下有可能不執行，因為事件沒有被觸發或者條件不滿足。

## callback 函數的使用場合

* 函數需要同步處理時
* setTimeout的延遲時間為0，這經常被用到，settimeout 呼叫的函數其實就是一個callback 的實作，類似範例可參考我的另一篇文章：[Javascript: setTimeout](http://smlsun.com/blog/2013/02/01/javascript-settimeout/)
* method chain：可參考：[jQuery method chain review](http://ithelp.ithome.com.tw/question/10090856)



另外，最好保證 callback 存在且必須是函數引用或者函數表達式：
(callback && typeof(callback) === "function") && callback();

## 使用上的技巧

因為 callback 的特性，如果你的函數傳入的參數不一致時將變得難以維護，建議函數在設計時應該盡量保持只有一個參數，若要傳入多參數則使用 json 來組合多個參數，然後統一有另一個參數用來傳入 callback 的函式。需注意在執行 callback 時需要先判斷該該參數是否為 function 若是才執行。
