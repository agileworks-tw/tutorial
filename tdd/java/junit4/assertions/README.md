# Assertion

JUnit 對於所有的 primitive type、object 跟（primitive type 或 object 的）array 提供 overload 的 assertion method。 參數的順序是期望值後頭接著實際值。 第一個參數可以是一個在失敗時輸出的字串。 有一個些微不同的 assertion 是 asserThat，他的參數有一個選擇性的失敗訊息、實際值、以及 Matcher object。 要注意的是，期望值與實際值的順序跟其他 assert method 是顛倒過來的。


下列是每一個 assert method 的典型寫法：

```
package sample;


import static org.hamcrest.CoreMatchers.*;
import static org.junit.Assert.*;

import java.util.Arrays;
import org.junit.Test;

public class TestAssertions {
    @Test
    public void testAssertArrayEquals() {
        byte[] expected = "trial".getBytes();
        byte[] actual = "trial".getBytes();
        assertArrayEquals("failure - byte arrays not same", expected, actual);
    }

    @Test
    public void testAssertEquals() {
        assertEquals("failure - strings are not equal", "text", "text");
    }

    @Test
    public void testAssertFalse() {
        assertFalse("failure - should be false", false);
    }

    @Test
    public void testAssertNotNull() {
        assertNotNull("should not be null", new Object());
    }

    @Test
    public void testAssertNotSame() {
        assertNotSame("should not be same Object", new Object(), new Object());
    }

    @Test
    public void testAssertNull() {
        assertNull("should be null", null);
    }

    @Test
    public void testAssertSame() {
        Integer aNumber = Integer.valueOf(768);
        assertSame("should be same", aNumber, aNumber);
    }

    // JUnit Matchers assertThat
    @Test
    public void testAssertThatBothContainsString() {
        assertThat("albumen", both(containsString("a")).and(containsString("b")));
    }

    @Test
    public void testAssertThathasItemsContainsString() {
        assertThat(Arrays.asList("one", "two", "three"), hasItems("one", "three"));
    }

    @Test
    public void testAssertThatEveryItemContainsString() {
        assertThat(
                Arrays.asList(new String[]{"fun", "ban", "net"}),
                everyItem(containsString("n"))
        );
    }

    // Core Hamcrest Matchers with assertThat
    @Test
    public void testAssertThatHamcrestCoreMatchers() {
        assertThat("good", allOf(equalTo("good"), startsWith("good")));

        assertThat("good", not(allOf(equalTo("bad"), equalTo("good"))));

        assertThat("good", anyOf(equalTo("bad"), equalTo("good")));

        assertThat(7, not(either(equalTo(3)).or(equalTo(4))));

        assertThat(new Object(), not(sameInstance(new Object())));
    }

    @Test
    public void testAssertTrue() {
        assertTrue("failure - should be true", true);
    }
}


```

其中關於 assert* 的函式第一個參數都可以指定 reason 讓每個判斷是都可以有個註解

使用

```
import static org.hamcrest.CoreMatchers.*;
import static org.junit.Assert.*;
```
讓 test case Assertion 更簡潔一點

## 範例專案

<https://github.com/agileworks-tw/spring-boot-sample/blob/master/src/test/java/sample/TestAssertions.java>

執行 `mvn -Dtest=TestAssertions test`
