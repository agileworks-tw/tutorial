# what is this

JavaScript 的 code 寫多了，你一定會碰到 this 這個關鍵字，是某個 object 下的 method 也好，或是 callback function 也好，關於 this 的用法常常會讓人搞混。

以一句簡單的話來說：在 function 裡，this 所代表的就是呼叫這個 function 的東西。

這樣講可能有點抽象，大家來看個實際的例子：

## this 是 window 的情況

```javascript
    <input type ="button"  id ="aButton"  value ="demo" onclick="" />
    <script type ="text/javascript" >
        function  demo()  {
            this.value  =  Math.random();
        }
    </script>
```

如果直接調用demo() 函數，tihs.value 將不存在，因為 demo 函數是在 window 對像中定義的，在簡單來說就是屬於全域，所以demo的擁有者（作用域）是 window(代表全域)，demo 裡的 this 也就是 window。 而 window 是沒有 value 屬性的。

更進一步的來看簡單的例子：

## this 不是 window 的情況

```javascript
<input type="button" id="aButton" value="demo" />
<script  type="text/javascript">
	var button = document.getElementById("aButton");
	function demo()  {
	  this.value = Math.random();
	}
	button.onclick =  demo;
	alert(button.onclick);
</script>
```

在此例中 this 代表的是 button，因為是透過函數指定的方式 button.onclick =  demo 來呼叫 demo()，他的上層是 button，所以也就有 value 的屬性


對於 button.onclick 輸出得到的是：

```javascript
  function demo() {
      this.value = Math.random();
  }
```

也就代表 demo() 屬於 button 的

## this 又是 window 的情況

```javascript
<input type="button" id="aButton" value="demo" onclick="demo()" />
<script type ="text/javascript" >
    var button = document.getElementById("aButton");
    function demo ()  {
        this.value = Math.random();
    }

    alert(button.onclick);
</script>
```

得到的輸出是：

```javascript
function onclick() {
    demo();
}
```

onclick ="demo()" 引用的方式中，onclick 事件只是直接調用 demo() 函數，而 demo() 函數的作用域仍舊是 w​​indow 對象，所以 this 仍然指向 window。


接著我們來看另一個特殊的情形...

## setTimeout 中的令人困惑的 this


```javascript
	function TT() {
		this.lm = "the message";
		this.startT = function() {
			setTimeout(function(){alert(this.lm);},500);
		}
	}

	TT();
	// this 則為 window 所以 this.lm = "the message"; 中的 lm 會被指向 window 而不是 TT 這個 object

	var d = new TT("the message");
	// this 是 Object 所以 this.lm = "the message"; lm 被正確建立於 TT 上

	d.startT();
	// d 在 window 底下，this 是 window。why??
```

在上面的例子中如果直接使用 TT()，this 指的是 window，如果透過 new，他所做的事就是先 new 一個 Object 接著將 this 指向這個 Object，這就是 new TT("the message") 當下 this 的由來… 所以在 第 2 行的 this.lm 則 ok。

但是很不幸的 d.startT(); 執行時在 d.startT();裡面的 this.lm 會是 undefind…

因為：

setTimeout其實是 window.setTimeout() 函數，並不是某個物件觸發的事件，在這種情況下，this 就會指向 window，因為當你呼叫 setTimeout 時，該函數裡的任務會被加入執行對列等候執行，一旦時間到開始執行實際上並不是經由 TT 來觸發而是全域的 window。

經由下列的測試可以證明：

``` javascript
setTimeout(function() { this.alert(this.document.body.innerHTML); }, 100);
```

又可以this.alert，又有this.document可用，表示 this 在當時指向的是 window。

既然如此我們要怎麼解決此問題？？？


## 解決 setTimeout 中的 this 是 window 的情況

```javascript
	function TT() {
		this.lm = "the message";
		var that = this; // 重點！
		this.startT = function() {
			setTimeout(function(){alert(that.lm);},500);
		}
	}
	var d = new TT("the message");
	d.startT();
```

利用 closure 關閉的是變數的概念，我們只要在外面宣告 ``var that = this;``，此時原本的 this 就會變為區域變數 that，當 setTimeout 執行函數時因為 that 因為 closure 的特性讓 setTimeout 存取操作 that 也就是 TT 的屬性，解決直接在 setTimeout 中使用 this 造成對象錯誤的情形。

接著剛剛有提到「沒指定的話」就是函數當前的作用域，所以這也就代表了「可以指定」，透過...

## call() 和 apply()  ##

``call()`` 和 ``apply()`` 的差別主要在於 ``call()`` 只接受一個參數，即 ``call(thisArg);``而 apply() 接受兩個參數，即 ``apply(thisArg, argArray)`` 。透過 call() 和 apply() 調用函數的主要目的，在於改變函數內部的 this 名稱所指涉的對象。對一般函數而言，當 programmer 在函數內部使用 this 名稱時，指涉對象是 global object 。global object 是運行環境中最頂層的個體，在瀏覽器環境中，global object 就是 window 此一個體。但是 ``call()`` 和 ``apply()`` 可以改變 this 名稱所指涉的對象。

其中在 ECMAScript Language Specification - Standard ECMA-262 3rd Edition. 15.3.4.3 & 15.3.4.4，有一段解釋：

>If thisArg is null or undefined, the called function is passed the global object as the this value. Otherwise, the called function is passed ToObject(thisArg) as the this value.

接著我們分別透過 ``call()`` 和 ``apply()`` 來驗證一下


* call()

```javascript
function myFunc() {
    window.alert(this.toString());
}

myFunc();

var hello = 'hello world';
myFunc.call(hello);
```

``myFunc();``未指定的情狀下，this 輸出的是 window， ``myFunc.call(hello);``則輸出 hello world


* apply()

    以下面這段程式碼為例：

```javascript
var foo = function(x) {
    alert(x);
    alert(this);
}
foo('abc');
```

你應該會看到訊息視窗先顯示 abc，接著就是顯示出 window。但若是變成下面這樣呢？

```javascript

var foo = function() {
    alert(arguments[0]);
    alert(this.name);
}
var bar = { name: 'bar' };
foo.apply(bar, ['abc','def']);
```

在呼叫 foo 函式時使用 apply 方法，就可以更換 caller（正確地說是切換 context），而因為用了 apply 方法，函式的參數就要改以陣列傳入。當然，這時候的 this 就變成了 bar。

 結果證實規範內容所言無誤。因此，我們可以利用 call() 和 apply() 改變函數內部的 this 名稱所指涉的對象。

而call跟apply的差別，就在於apply的第二個參數是陣列，而call則是一個一個指定參數例如：

* call 呼叫的話會變成；``myFunc.call(hello,"abc","def");``
* apply 的好處是可以先把陣列準備好，如 ``foo.apply(bar, ['abc','def']);``，然後重覆使用。



資料來源：


* [石頭閒語][1]
* [棕熊@Think Fast][2]
* [ericsk.net][3]

此篇文章是把上面三個來源的內容進行融合，挑選比較淺顯易懂得部分，加上我個人的淺見跟理解過後加以補述，希望可以幫助對於 this 不是很清楚的人。



  [1]: http://blog.roodo.com/rocksaying/archives/2532303.html
  [2]: http://www.cnblogs.com/ruxpinsp1/archive/2008/04/20/1162463.html
  [3]: http://blog.ericsk.org/archives/1360
