# setTimeout


在使用 setTimeout 時，假設要執行 4 次就如同下面的例子：


```javascript
  for (var i = 0; i < 4; i++)
  {
      console.log("A="+i);
      function A(){
          console.log("B="+i);
      }
      window.setTimeout(A, 0);

  }
```

一般常理判斷結果應該是：

	A=0
	B=0
	A=1
	B=1
	A=2
	B=2
	A=3
	B=3



實際結果如下：

	A=0
	A=1
	A=2
	A=3
	B=4
	B=4
	B=4
	B=4

有沒有覺得很奇怪?


這是因為 javascript 屬於單執行序，看起來 ``window.setTimeout(A, 0);`` 似乎是馬上執行，但是實際上， for 迴圈裡的 setTimeout 會先放在代執行的堆疊裡，直到 for 迴圈結束，但如此一來到結束時，i 即為 4，所以結果就是堆疊裡的每個待執行任務中的 i 都為 4。


所以比較好的寫法應該是：

```javascript
  var i = 0;
  function doAppend()
  {
      if (i++ >= 4){
          return;
      }
      console.log("B="+i);
      setTimeout(doAppend, 0);
  }
  setTimeout(doAppend, 0);
```


跟上面的例子有什麼不同？上面的 setTimeout 每個是獨立的，這個例子的 setTimeout 將 一環接著一環，如此一來，每個 setTimeout 都會有正確的 i 了

關於 javascript 事件驅動以及運作方式想更進一步了解，可參考以下文章

[JavaScript可否多線程? 深入理解JavaScript定時機制](http://www.phpv.net/html/1700.html)

另外一旦我們想要清除定時器，可以通過將定時時產生的ID標識傳遞給clearTimeout或者clearInterval函數來清除定時，至於使用哪個函數取決於調用的時候使用的是setTimeout還是setInterval。範例如下：

	var id = setTimeout ( foo ,  1000 );
	clearTimeout ( id );

假設我們要清除所有定時器，但由於沒有內置的清除所有定時器的方法，可以採用一種暴力的方式來達到這一目的。

	//清空"所有"的定時器
	for ( var i =  1 ; i <  1000 ; i ++)  {
		clearTimeout ( i );
	}

可能還有些定時器不會在上面代碼中被清除（如果定時器調用時返回的ID值大於1000），因此我們可以事先保存所有的定時器ID，然後一把清除。
