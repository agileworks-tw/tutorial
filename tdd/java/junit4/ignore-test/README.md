# 略過 test

在某些狀況下，你會希望跳過 Test

在 JUnit 中要略過一個 test，你可以把 method 給註解掉、刪除 @Test annotation。

不過 test runner 也就不會回報這個 test。另外一個方法是加 @Ignore 這個 annotation。

如果你想要紀錄這個 test 為什麼要略過，@Ignore 可以傳入一個字串作為記錄。

```
@Ignore("Spooky: 暫時略過")
@Test
public void testSame() {
    assertThat(1, is(1));
}
```
