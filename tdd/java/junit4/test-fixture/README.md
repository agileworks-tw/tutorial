# test fixture

test fixture 用來作為執行測試前的準備工作。目的是確保測試的環境是可重覆驗證，這樣測試結果才會是可重複的。可能使用情境如下：

* 準備輸入資料、建立或設定 mock object。
* 載入一組指定、已知的 database 資料
* 複製一些指定的檔案


JUnit 提供 annotation 給 test class 指定在每個測試前後的 fixture、 或是在執行所有 test method 前先執行一次性的 fixture。

總共有四個 fixture annotation，分為兩個 level：

## class level

`@BeforeClass` 跟 `@AfterClass`

在 class level 可以進行資料庫連線相關，或是 fake / mock object。

## method level

`@Before` 跟 `@After`

在 method level 只要有定義上述 annotation 每次進行 test method 時必會進行，可用於準備測試資料，並在測試完成後進行銷毀。

## 使用範例

``` java
package test;

import java.io.Closeable;
import java.io.IOException;

import org.junit.After;
import org.junit.AfterClass;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class TestFixtures {

    //  進行函式的 Mock
    static class ExpensiveManagedResource implements Closeable {
        @Override
        public void close() throws IOException {}
    }

    static class ManagedResource implements Closeable {
        @Override
        public void close() throws IOException {}
    }

    private ManagedResource myManagedResource;
    private static ExpensiveManagedResource myExpensiveManagedResource;


    @BeforeClass
    public static void setUpClass() {
        System.out.println("@BeforeClass setUpClass");
        myExpensiveManagedResource = new ExpensiveManagedResource();
    }

    @Before
    public void setUp() {
        System.out.println("@Before setUp");
        this.myManagedResource = new ManagedResource();
    }


    @Test
    public void test1() {
        System.out.println("@Test test1()");
    }

    @Test
    public void test2() {
        System.out.println("@Test test2()");
    }

    @After
    public void tearDown() throws IOException {
        System.out.println("@After tearDown");

        this.myManagedResource.close();
        this.myManagedResource = null;
    }

    @AfterClass
    public static void tearDownClass() throws IOException {
        System.out.println("@AfterClass tearDownClass");
        myExpensiveManagedResource.close();
        myExpensiveManagedResource = null;
    }

}
```

## 範例專案

<https://github.com/agileworks-tw/spring-boot-sample/blob/master/src/test/java/sample/TestFixturesExample.java>

為了讓學員容易理解，輸出結果就如上面程式碼所排列的順序一樣

執行 `mvn -Dtest=TestFixturesExample test`

將輸出下列訊息

```
@BeforeClass setUpClass
@Before setUp
@Test test1()
@After tearDown
@Before setUp
@Test test2()
@After tearDown
@AfterClass tearDownClass
```
