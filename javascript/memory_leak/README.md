# javascript: Memory Leaks 的情況以及如何解決與偵測


文章來源：

* [簡單理解 JavaScript 的記憶體管理機制](http://fred-zone.blogspot.tw/2012/05/javascript_22.html)
* [配合GC，JavaScript性能優化之：邪惡閉包，對象引用清除深入探究](http://www.ppzhang.com/?p=8)


若要知曉如何避免 Memory Leaks 就要先了解 ...

## JavaScript 的記憶體管理機制

不像其他的語言，JavaScript 開發者永遠沒有辦法自己去釋放記憶體，頂多只能移除物件的 Reference （代表這物件已經沒有人在使用），而且這物件所佔的記憶體並不會馬上被釋放，而是 Garbage Collection 在滿足某些條件的情況下，才在背景自動去尋找沒有被使用的物件，然後釋放。若你嘗試過尋找釋放記憶體或移除物件 Reference 的方法，得到的解答，應該不外乎是使用 delete 關鍵字或是將變數設為 null，若在不瞭解的情況下使用它們，可能因此產生 Memory leaks 的狀況。JavaScript 的記憶體管理機制，更準確的說，是物件的管理機制。

從 JavaScript 開發者角度來看，JavaScript Engine 在運作時，記憶體使用是呈現樹狀結構，也就是所有命名或建立的變數或物件，都是存放在一個全域(global)的 Object 中。

我們可以做個實驗理解一下：

```
	var myVar = 'Hello';
	function myFunc() {
		return 123;
	}
	var myObj = {
		a: 1,
		b: 2
	};

	console.log(global);
```

執行以上程式，你應該可以從 global 中找到我們自己定義的變數和函式：

```
	{
		...（已省略基本預設的環境變數）...
		myVar: 'Hello',
		myFunc: [function],
		myObj: {
			a: 1,
			b: 2
		},
		...
	}
```

從結果可以發現，所有的物件都以樹狀的形式被 global Object 保存著，無論是變數還是任何一種類型的物件，都是一組組 Key/Value 的存在。而 Value 就是各種不同形態的物件，如字串、函數、陣列、數值等。

所以，移除某物件的 Reference，就意味著將把物件從這棵樹上拔除掉。因此，我們可以直接將該變數設為 null：

`myVar = null;`

由於該變數被設為 null，原本的字串（包含著『Hello』）物件就失去了依附的樹枝，如枯葉般從樹上掉下來，等著 Garbage Collection 來回收它。對於開發者而言，其實就是告訴 GC 我不需要這物件了，隨時可以把這個物件的記憶體釋放。

然而，雖然變數被設為 null 後，原本的物件被釋放了，但該變數還是存在的，別忘了，他是一個在 global Object 中的 Key，現在只是沒有 Value 為 null 而已。要真正把這個變數給刪除，這時就要用到 delete 關鍵字。如果你去查一下 JavaScript 的 API 參考文獻，就會發現 delete 關鍵字其實是拿來刪除 Object 中的一組 Key/Value。因此，既然 JavaScript 所有的變數其實都只是一組存放在 global Object 的 Key/Value，我們理所當然可以用 delete 關鍵字去移除掉他：

`delete myVar;`

了解了 JavaScript 的記憶體管理機制後，你就會了解使用 delete 關鍵字和將變數設為 null，其實並不是代表物件就會被釋放，只是砍樹枝去減少物件的 Reference。

此外，如果一個物件有多個 Reference，只是單單刪其中一個也不會讓物件被 GC 釋放：

```
	var myVar = 'Hello';
	var myVar1 = myVar;

	myVar = null;
	delete myVar;

	console.log(myVar1);
```

以上的程式會顯示『Hello』字串，該物件並不會因為失去 myVar 這 Reference 而被 GC 移除。若想要這一個字串被釋放，必需清空物件所有的 Reference（包括 myVar 和 myVar1），才能讓物件具有被 GC 回收的條件。所以，如果你不小心讓一個不明顯的變數勾搭上了物件，然後你忘記了這個變數的存在，很有可能就會造成 Memory Leaks，讓以為已經被釋放的物件，偷偷存活在於記憶體上。

其中 Reference 是常見於各種系統的設計，主要做法是幫物件建立一個 Reference 計數器，當有人關聯或使用到他，就會讓這計數器加一，等到關聯被移除或使用完畢後，就會讓計數器減一。所以，一旦計數器為零時，代表現在沒有任何外部的物件在使用或關聯到它，是可以被釋放掉的狀態。


對於記憶體的管理機制了解之後，接著看 ...

## GC 的判定方式

mark-and-sweep（標記清除）算法，即：

（1）遍歷所有可訪問的對象。

（2）回收已不可訪問的對象。

實際運作上，就如同上一節有講到的，透過檢查計數器是否為 0 來確認是否可以進行 GC

正常來說，如果有確實將全域變數的 Reference 正確清除的話，記憶體應該會被 GC。



## 如何避免無法 GC 的情形？

1. 定義變數一定要用 var，否則預設宣告出來的變量都是全域變量，不是區域變數
2. 全域變數沒用時記得要指定為 null，確實將全域變數的 Reference 正確清除
3. 正確使用 delete ，刪除沒用的一些函數屬性；
4. window.open 出來的視窗即使 close 了，它的 window 對象還是存在的，要記得刪除引用；
5. frame 和 iframe 的情況和 window.open 的情況類似。

## 如何透過工具偵測 leaks 情形？

下面例子是全域變數之 Reference 沒有確實清除的情形：

```
	function Library(name){
		this.name = name;
	}
	var PIPI = {
		Mapping : [],
		get : function(){
			 return PIPI.Mapping[0];
		}
	}
	var externLib = new Library("0000");
	PIPI.Mapping.push(externLib);
	(function(){
		var lib = PIPI.get();
		lib = null;
		var lib2 = PIPI.Mapping[0];
		lib2 = null;
	})();
```

一旦上面得程式碼執行後，可以透過 chrome 的開發者工具中的 Profiles 來觀看變數的使用情形，如下圖：

![img](https://lh5.googleusercontent.com/-1I9sdsmLfxo/USCnHcVdzVI/AAAAAAAALhs/1udovkwXtfE/s604/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7+2013-02-17+%E4%B8%8B%E5%8D%885.43.34.jpg)

可以看到，有兩個 library 對象：一個是函數宣告，另外一個才是 ``new Library("0000")``，下面的 Retaining tree 呈現有哪些物件引用了 ``new Library("0000")``，分別是外部變數 externLib 以及 ``PIPI.Mapping[0]`` (圖中樹狀從節點往 root)。

透過該工具的協助既然知道了有哪些 Reference 沒有確實清除，要解決此問題就簡單多了只要加入：

```
	PIPI.Mapping[0] = null ;
	externLib = null ;
```

將 Reference 清除，完成程式碼如下：

```
	function  Library(name){
			this .name = name;
	}
	var  PIPI = {
		Mapping : [],
		get : function (){
			 return  PIPI.Mapping[0];
		}
	}
	var  externLib = new  Library( "0000" );
	PIPI.Mapping.push(externLib);
	//此時new Library("0000")對像有2個引用
	( function (){
		var  lib = PIPI.get();
		//引用數+1：3
		lib = null ;
		//引用數-1：2
		var  lib2 = PIPI.Mapping[0];
		//引用數+1：3
		lib2 = null ;
		//引用數-1：2
		PIPI.Mapping[0] = null ;
		//引用數-1：1
		externLib = null ;
		//引用數-1：0
	})();
```

接著我們在用 chrome 的開發者工具檢視，如下圖：

![img](https://lh5.googleusercontent.com/-LMw8XLJlJBM/USCnHEzC08I/AAAAAAAALhk/RAo0i4Yi97k/s604/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7+2013-02-17+%E4%B8%8B%E5%8D%885.31.45.jpg)

可以看到原本除了宣告函數存在之外，另一個變數已消失，表示 leaks 的情形已被解決！當然上述的狀況說明的是關於全域變數如果要確實 GC 的方式，關於區域變數，照理來說一旦所屬函數被執行完之後，區域變數應該會馬上被回收，要注意的是如果是有 closure 的情形，如果 closure 未被執行，表示函數尚未完全執行結束，也就代表區域變數無法被正確回收，這點必須特別注意，也因此再次強調使用 closure 要特別小心 leaks 的情形。

另外只要將游標指向你欲查看的變數上面，profiles 將顯示該變數被宣告的程式檔與行號，透過超連結，可以直接開啟，可以方便找出有問題的全域變數位置。


其中針對圖中的欄位解釋如下:

* Shallow Size: 對象自身佔用的內存大小，不包括它引用的對象。

	針對非數組類型的對象，它的大小就是對象與它所有的成員變量大小的總和。當然這裡面還會包括一些語言特性的數據存儲單元。針對數組類型的對象，它的大小是數組元素對象的大小總和。

* Retained Size: 當前對像大小 + 當前對象可直接或間接引用到的對象的大小總和。

	間接引用的含義：A->B->C，B 是直接引用，C 就是間接引用；換句話說，Retained Size 就是當前對像被 GC 後，從 Heap 上總共能釋放掉的內存。


> 一旦客戶說速度變得異常的慢，記憶體標高時，就是時候分析客戶目前瀏覽器關於記憶體使用的 profile，麻煩使用者改用 chrome 在關鍵時刻，請他將瀏覽網頁 snapshot 起來分析一下囉！
