# git tag 指令

標籤

### 使用情境

* 里程碑管理
* 準備發佈一個穩定版本，給予容易識別的版本命名

### 命名

```
[主版本號].[次版本號].[修訂版本號]
```

```
v0.0.1
// or
v0.0.1
```

### 常用範例

| 範例                     | 說明     |
|------------------------|--------|
| git tag                |        |
| git rev-parse v0.0.1   |        |
| git tag v0.0.1 sha1234 | 新增 tag |
| git tag -d v0.0.1      | 刪除 tag |


```
$ git rev-parse v0.0.1
d93a61550216134ea18ff5db907f066fd8beb866
```

```
$ git cat-file -p d93a61550216134ea18ff5db907f066fd8beb866

tree cbfd7a8e6c7bd0eec9f524b42bdce9ff31bac2e3
parent 59da3738f9ccf00e1246098a65259b713e848926
author alincode <alincode@gmail.com> 1526267514 +0000
committer alincode <alincode@gmail.com> 1526267514 +0000

add hello2 file
```

### 語法結構

```
usage: git tag [-a | -s | -u <key-id>] [-f] [-m <msg> | -F <file>] <tagname> [<head>]
   or: git tag -d <tagname>...
   or: git tag -l [-n[<num>]] [--contains <commit>] [--points-at <object>]
                [--format=<format>] [--[no-]merged [<commit>]] [<pattern>...]
   or: git tag -v <tagname>...

    -l, --list            list tag names
    -n[<n>]               print <n> lines of each tag message
    -d, --delete          delete tags
    -v, --verify          verify tags

Tag creation options
    -a, --annotate        annotated tag, needs a message
    -m, --message <message>
                          tag message
    -F, --file <file>     read message from file
    -s, --sign            annotated and GPG-signed tag
    --cleanup <mode>      how to strip spaces and #comments from message
    -u, --local-user <key-id>
                          use another key to sign the tag
    -f, --force           replace the tag if exists
    --create-reflog       create a reflog

Tag listing options
    --column[=<style>]    show tag list in columns
    --contains <commit>   print only tags that contain the commit
    --merged <commit>     print only tags that are merged
    --no-merged <commit>  print only tags that are not merged
    --sort <key>          field name to sort on
    --points-at <object>  print only tags of the object
    --format <format>     format to use for the output
```