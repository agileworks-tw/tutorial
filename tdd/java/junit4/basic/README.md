# JUnit 4 基礎

JUnit 是元老級的 Java 單元測試框架，大多數的 Java IDE 與建置工具（Build tools）都支援 JUnit，例如下列的軟體對 JUnit 都有原生的支援：

Java IDE

* IntelliJ IDEA
* Eclipse

Build tools

* Maven
* Gradle

DevOps

* Jenkins CI

## Java Class

File Name: `Calculator.java`

```java
public class Calculator {
  public int evaluate(String expression) {
    //TODO
  }
}
```

## Test Case

File Name: `CalculatorTest.java`

```java
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class CalculatorTest {
  @Test
  public void evaluatesExpression() {
    Calculator calculator = new Calculator();
    int sum = calculator.evaluate("1+2+3");
    assertEquals(6, sum);
  }
}
```

## Compile and Run Test

```
# Compile
javac Calculator.java
javac -cp .:junit-4.XX.jar CalculatorTest.java

# Run Test
java -cp .:junit-4.XX.jar:hamcrest-core-1.3.jar org.junit.runner.JUnitCore CalculatorTest
```

## Final Java Class

因為有 Test Case，因此在 `evaluate` 方法的撰寫就有更清楚的目標：完成第一版可以通過測試的程式。

File Name: `Calculator.java`

```
public class Calculator {
    public int evaluate(String expression) {
        int sum = 0;

        for (String summand: expression.split("\\+")) {
            sum += Integer.valueOf(summand);
        }

        return sum;
    }
}
```

重新跑一次測試。

## 參考資料

* [JUnit 4 Wiki: Getting Started](https://github.com/junit-team/junit4/wiki/Getting-started)
* [JUnit 4 Wiki 中文翻譯](http://junit.dontcareabout.us/Getting-started.html)
