# 使用者驗證設置

## 建立 ssh key

`ssh-keygen -t rsa`

預設會產生在 `~/.ssh` 將會有 `id_rsa`, `id_rsa.pub` 這兩個檔案

`id_rsa` 通常會用存在於 client，比如開發者 存取 gitlab，或是 Jenkins server 需要存取 gitlab 的情狀。

`id_rsa.pub` 需要存於 遠端 server，比如 staging server 或是 gitlab 使用者 ssh key。

## 以開發者存取 gitlab 為例，設置 gitlab ssh key 讓開發者可以透過 Clone with SSH 存取專案

git 通常提供下面兩種專案存取方式，若要透過 Clone with SSH 我們需要設置 ssh key

![](assets/2019-02-18-17-08-55.png)

在 gitlab 登入特定使用者後，可以設置使用者專屬之 public ssh key，首先進入 Setting

![](assets/2019-02-18-17-11-09.png)

點選 SSH Keys 

![](assets/2019-02-18-17-11-42.png)

將 `id_rsa.pub` 內容貼到畫面輸入區塊，可透過下面指令

`cat ~/.ssh/id_rsa.pub` 

將看到類似內容

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCjS2fVg0mgAshipeLNWDJEW5oW9aPpgBDWk9l7mjfz+lLf70x+8jtnlaMLbKxQNPwNAj6FqaOjW5QtWYCcUZv3tvPMaBUHLjpaS/MLiq6EplNQNXuTfaKSFBoUwHiOP/RR1Nji7pixLTDhSlMC0Qfe+2CsMp+zyPz7Ix0y608wIpJerfp9e+i1baoWb97Vepmw+hr/L+IDV4pilGPp8cLk1Er4eP4tgup9wkOt5hUI38XdL4xIS64NNUEhOs5mMyiBqiW/JmXaJdXRt7o8fjGvGhtXdjXWrva1UnEBQoPqV4xiOwhDg1KS0QPCOU5RpBBWGkqR8eZgm/bIuMehvPI5 jenkins@ubuntu-bionic
```

貼上後畫面如下：

![](assets/2019-02-18-17-14-19.png)

接著我們可以試著驗證 git clone 是否可以運作

`git clone ssh://git@gitlab.trunksys.com:30001/agileworks/spring-boot-sample.git`

正常取出專案原始碼，表示設置正常


## Jenkins server 需要存取 gitlab 為例

點選主頁之 Credentials

![](assets/2019-02-18-17-19-31.png)

點選右邊區塊 Jenkins 連結

![](assets/2019-02-18-17-20-54.png)

![](assets/2019-02-18-17-21-29.png)

點選 Global credentials

![](assets/2019-02-18-17-22-05.png)

點選 Add Credentials

![](assets/2019-02-18-17-22-37.png)

輸入 Private Key，可透過下面指令取得

`cat ~/.ssh/id_rsa` 

範例輸出如下

```
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAo0tn1YNJoALIYqXizVgyRFuaFvWj6YAQ1pPZe5o38/pS3+9M
fvI7Z5WjC2ysUDT8DQI+hamjo1uULVmAnFGb97bzzGgVBy46WkvzC4quhKZTUDV7
k32ikhQaFMB4jj/0UdTY4u6YsS0w4UpTAtEH3vtgrDKfs8j8+yMdMutPMCKSXq36
fXvotW2qFm/e1XqZsPoa/y/iA1eKYpRj6fHC5NRK+Hj+LYLqfcJDreYVCN/F3S+M
SEuuDTVBITrOZjMogaolvyZl2iXV0be6PH4xrxobV3Y11q72tVJxAUKD6leMYjsI
Q4NSktEDwjlOUaQQVhpKkfHmYJv2yLjHobzyOQIDAQABAoIBABGz/hjOt++p/ZF8
TH9YnXJ9v9HXZaLN6IVq1/wndwNzUwLGDbQBjOEo/tkhOfkkFWNPp/mTr5LpPcJA
3smTq2YKppm1evohT+A0NbA9o7fr1EJw2eneh/5wQXeYejlpw5IPkkff+BvVO2Rh
S2iVwtWwyQVCI8A4/Pw5DVRU4GvmV0NszPSb1WZx2QRKKgIQA1IBUhZp1MOF8iEH
Hl4kNjDChUEYcYD6B8ANk0b46Aqrm+epWPmMQYGXuhHYDXfc129O72blY1j+1wRx
UadXmS+f/Zv6cnJhi4nPuAj8M/DWQb6DNd3ffp2EbLfhIQMt41FtK4ri9ZkAXihF
TTdVIyUCgYEAz9GXxNrTAPnmRewWGRZvgJeZUqj0tBeHerLmNw1xKVuYdxTbEUfw
/DKSuYwwyNZVY5BBbye6f3euZKmCZTY4q1O9Zw6ppYG2zMdF2EiMD4p0pUp47bUd
xwxd8jeNczWgq6pvXwZ1NUR7e2kc+d1R0YEoJWnUa2jJ2bJCvR6+qRMCgYEAySc5
lAWSh5eGZtzgqWG47wOqEPLlkDykAggOLvpQqqbcj7JD7zlAL7kRg43nDk+8/JyD
cG9AHD/x4qT4iOXQyloxidaLJ6seN6eZjJuWvWR8oS5Q5PGuqZNvcD34e1srmOFp
txt/TmE2gF/RY68zD4xA+2UPvC99ZivrRK3JDQMCgYBLWYEfvP+YcQNPAuSYQAw5
ob3TvLLMwWM717Wk7FjFWBKVypgLUfxMVMHiSLQ/fYcETH+NH+h84xX2JYfDzr8J
T5lyzlwwSDHRWcc3PkaaM+dLLw9dkLe1PgSqF/5PcXhKBcfPunWw1J25B0mcRuSt
g5jcx9xe/WWCayHLlGQoxQKBgAua5LqCe8qw1kM2+QsspSO8/WHO8amZpgir+E2D
iYXe7Jipuzug/PAD6FvDoxHzTb7xNLAW6wb2NXlS9TfIsnwKKhN+ujaGq86gL76p
909j7cDK0EX1H5OO+v3pxV0wjFpcnuG+h2C5QRC09nqez/5UpCcc1ISR5NUxMXib
4h6LAoGBAIWyN0VKmZTNFikgPs0ddeXMrz++PvEzCe9t418Qi82N8Acgd3LlKbIy
G1bJkZcqAvplJ3CJ9npkTj8CSb9AosSqY8Vo8H26pxRxeSFzQVHRqVVJv2KTHLIA
/LC/+x4sOvFEIO8jYTctNMxcyyRWvcJYTjWsSDdsJR1ErYPKgX+R
-----END RSA PRIVATE KEY-----
```

輸入完成畫面：

![](assets/2019-02-18-17-24-53.png)

其中 Username 需要與上一步驟之 gitlab username 相同方可驗鄭成功，點選 OK 完成。

在 Jenkins 新增 Jobs 點選 git，設定如下

![](assets/2019-02-18-17-26-42.png)

若無紅色字警告表示設置正常，Jenkins 已可正常存取 gitlab

