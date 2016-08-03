# Junit Suite

當 JUnit 有多個或所有的 Test Case 要執行，此時就需要 Test Suite 來管理眾多的Test Case，Suite 可以用來管理 Test 的執行順序，也可以在所有 Test Case 開始或結束之前，統一進行設置。

## Sample 專案

<https://github.com/agileworks-tw/spring-boot-sample>

## 新增 SuiteTest Class 定義 Test 執行順序


```
@RunWith(Suite.class)
@Suite.SuiteClasses({
        BTest.class,
        ATest.class
})
public class SuiteTest {
}
```

其中在

```
@Suite.SuiteClasses({
        BTest.class,
        ATest.class
})
```

所設定的 Test Class 的順序，將會依序進行，在沒有使用 SuiteTest 之前 Junit 將會根據 Class 字母依序執行，其執行順序為：

1. ATest.class
2. BTest.class

使用了上述程式碼的定義，執行順序將會調整為

1. BTest.class
2. ATest.class

如此一來，就可以根據實際狀況調整 test 執行的順序。

## 進行測試前後設置

在 SuiteTest Class 中可以在所有測試開始之前，以及所有測試結束之後進行統一的設置

經由使用 `@BeforeClass` 及 `@AfterClass` 來完成相關作業，程式碼如下：

```
@RunWith(Suite.class)
@Suite.SuiteClasses({
  BTest.class,
  ATest.class
})
public class SuiteTest {
    @BeforeClass
    public static void setUpClass() {
        System.out.println("=== Master setup ===");
    }

    @AfterClass
    public static void tearDownClass() {
        System.out.println("=== Master tearDown ===");
    }
}
```

運行 Test 的情況會為：

1. SuiteTest.setUpClass
2. BTest.setUpClass
3. BTest 執行測試
4. BTest.tearDownClass
5. ATest.setUpClass
6. ATest 執行測試
7. ATest.tearDownClass
8. SuiteTest.tearDownClass

如此一來，我們就可以在所有 Test 開始前，進行如測試資料的準備，或是預先連接相關測試服務，方便進行測試。
