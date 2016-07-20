# checkStyle

## maven POM.xml 設定
```
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-checkstyle-plugin</artifactId>
  <version>2.9.1</version>
  <executions>
      <execution>
      <id>checkstyle</id>
      <phase>validate</phase>
      <goals>
          <goal>check</goal>
      </goals>
      <configuration>
          <failOnViolation>false</failOnViolation>
      </configuration>
      </execution>
  </executions>
</plugin>
```
