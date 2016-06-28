# javascript: closure

####資料來源

* [Gossip@caterpillar](http://caterpillar.onlyfun.net/Gossip/JavaScript/Closure.html)
* [一句話說 JavaScript 中的 Closure](http://hi.baidu.com/jz1108/item/e549ca105c4c6bf89c778ab6)
* [搞清楚lexical scope與closure](http://blog.ithome.com.tw/index.php?op=ViewArticle&articleId=19392&blogId=257)


## 什麼是 closure

JavaScript 中的 closure 是初學者比較難理解的觀念，下面是幾個來源關於 closure 的解釋：

* A ``closure`` is created when a function ``keeps a link to its parent's scope`` even after the parent has returned.
  > Object-Oriented JavaScript
* A closure is a protected variable space, created by using nested functions.
  > Pro JavaScript Design Patterns
* A closure is a way to access and manipulate(操作) external variables from within a function.
  > Secrets of the JavaScript Ninja
* Closures are means through which inner functions can refer to the variables present in their outer enclosing function after their parent functions have already terminated.
  > Pro JavaScript Techniques
* A closure is a special kind of object that combines two things: a function, and the environment in which that function was created.
  > MDC
* A closure is a way to access and manipulate(操作) external variables from within a function.
  > Secrets of the JavaScript Ninja
* A "closure" is an expression (typically a function) that can have free variables together with an environment that binds those variables (that "closes" the expression).
  > jibbering.com


``` javascript
  function doSome() {
    var x = 10;
    function f(y) {
      return x + y;
    }
    return f;
  }

  var foo = doSome();

  foo(20); //輸出結果為 30
  foo(30); //輸出結果為 40
```

上面 doSome 的例子中，f 建立了一個 closure，如果你單看：

``` javascript
  function f(y) {
      return x + y;
  }
```

看來起 x 似乎沒有定義。實際上，x 是從外部函式捕捉而來。closure 是個捕捉了外部函式變數（或使之繼續存活）的函式。在上例中，函式 f 建立了 closure，因為它將變數x關入（close）自己的範圍。如果形式 closure 的函式物件持續存活，被關閉的變數 x 也會繼續存活。就像是延續了變數x的生命週期。

由於 doSome 傳回了函式物件並指定給 foo，就 doSome 而言已經執行完畢。單看 x 的話，理應 x 已結束其生命週期，但由於 doSome 中建立了closure並傳回，x 被關閉在 closure 中，所以 x 的生命週期就與 closure 的生命週期相同了。如上例所示， 呼叫 foo(20) 結果就是 10+20（因為被閉關的 x 值是 10 ），呼叫 foo(30) 結果就是 10+30。


更精簡的說明 Closure 就是擁有閒置變數（Free variable）的運算式，上面提到的例子中 x 就是所謂的 Free variable，什麼是 Free variable ？

參考這篇：[](http://stackoverflow.com/questions/12934929/what-are-free-variables)

> Free variables are simply the variables that are neither locally declared nor passed as parameter.

翻譯起來就是 Free variable 代表不是 function 的參數，x 之所以稱為 Free variable 也就是因為在 f 這個 function 外面被宣告，也沒有透過 function 的參數傳入，但是在 f 裡面卻可以存取。

另外 Closure 有 lexical scope 的特性，所謂的 lexical scope 就是讓我們可以用區域變數的方式，把變數當作一個 function 物件的 private member，但是又可以用一個 function 當作 getter/setter 來存取他，如同：

``` javascript
  function Bean() {
    var X;
    var Y;
    this.setX = function(x) {
      X=x;
    }
    this.getX = function() {
      return X;
    }
    this.setY = function(y) {
      Y = y;
    }
    this.getY = function() {
      return Y;
    }
  }

  var a = new Bean();
  a.setX(3);
  a.setY(3);
  alert(a.getX()+""+a.getY());
```

## closure 關閉的對象

closure 關閉(包起來)的是變數，而不是變數所參考的值。下面這個範例可以證明：

``` javascript
  function doOther() {
    var x = 10;
    function f(y) {
      return x + y;
    }
    x = 100;
    return f;
  }

  var foo = doOther();
  foo(20);
  foo(30);
```


直覺來看應該是 10+20，以及 10+30，實際上卻不是，因為在 建立closure時綁定的是 x 變數，而不是數值 10（x變數的值），也因此 doOther 之後改變了 x 變數的值，因此此時 x 的值已變為 100，而後執行 foo 就是用 x=100 在做運算，範例顯示的結果分別是 100+20 與 100+30。


並且由於 closure 綁定的是變數，所以你也可以在 closure 中改變變數的值：

``` javascript
  var sum = 0;
  [1, 2, 3, 4, 5].forEach(function(element) {
       sum += element;
   });

  sum; //變數內容為 15
```


如果closure關閉了某個變數，使得該變數的生命週期得以延長，那麼這個會怎麼樣？

``` javascript
  function doOther() {
    var x = 10;
    function f() {
      x--;
      return x;
    }
    return f;
  }

  var f1 = doOther();
  var f2 = doOther();

  f1();
  f2();
```


在這個範例中，doOther被呼叫了兩次（或更多次），doOther中的closure關閉了x，並對其執行了遞減。呼叫了f1時，x會被遞減1，所以顯示9，這沒有問題，那麼呼叫f2()後，結果是9？

像這類的例子，其實結果是一致的，關閉的是建立closure時外部範圍下的變數。以上例來說，第一次呼叫doOther時，建立了x變數(新的記憶體位置)，指定值給x變數，而後建立closure將之關閉。第二次呼叫doOther時，建立了x變數(新的記憶體位置)，指定值給x變數，而後建立closure將之關閉。所以f1與f2關閉的根本是不同作用範圍的 x 變數（也就是該次呼叫 doOther 時所建立的 x 變數）。所以上例中，呼叫f2之後顯示的值仍是9。


## Closure 使用上需注意


* Closure 有可能會造成記憶體洩漏，主要是因為被參考的變數無法被垃圾收集機制處理，造成佔用的資源無法釋放，所以使用上必須考慮清楚，不要造成意外的記憶體洩漏。（在上面的例子中，如果 f1 一直未執行，使用到的記憶體 x 就不會被釋放）
* 跟透過函數的參數把變數傳給函數比較起來，Javascript Engine 會比較難對 Closure 進行最佳化。如果有效能上的考量，這一點也需要注意。
