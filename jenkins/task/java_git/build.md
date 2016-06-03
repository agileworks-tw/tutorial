# Build 自動建置

## 使用時機

1. Daily Build
2. 週期性建置
3. 進行正式機部署時事先建置

## Task 實作

先設置 git Repository 使用：

```
https://github.com/agileworks-tw/spring-boot-sample
```

### Shell 指令

```
#!/bin/bash
mvn package
```
