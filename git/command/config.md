# 設定檔


### 設定檔的位置

```
Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
```

* git config --global 的設定內容會被寫入 ~/.gitconfig
* git config 的設定會被寫入 .git/config
### 編輯設定檔的方式

* `vi .git/config`
* 使用 `git config` 指令

### 常用範例

| 範例                                                          | 說明         |
|-------------------------------------------------------------|------------|
| git config l                                                | 列出所有設定值    |
| git config push.default matching                            |            |
| git config --global user.name "demo_user"                   |            |
| git config --global user.email "demo_user@demo.com"         |            |
| git config --local user.name "demo_user"                    | 設定名稱       |
| git config --local user.email "demo_user@demo.com"          | 設定信箱       |
| git config alias.tree "log --oneline --decorate --graph"    | 設定 tree 暱稱 |
| git config alias.l "log --all --decorate --graph --oneline" | 設定 l 暱稱    |
| git config core.editor "vim"                                | 修改預設編輯器    |

### 推薦設定的 alias

```
alias.co=checkout
alias.ci=commit -m
alias.st=status
alias.pl=pull
alias.ps=push
alias.df=diff
alias.br=branch
alias.ap=add -p
alias.aa=add .
alias.cp=checkout -p
alias.cc=checkout .
alias.ss=stash
alias.spp=stash pop
alias.sdd=stash drop
alias.rb=rebase
alias.type=cat-file -t
alias.dump=cat-file -p
alias.clear=remote prune origin
alias.tree=log --oneline --decorate --graph
alias.cm=commit
alias.lg=log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --
alias.logg=log --all --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

### 語法結構

```
usage: git config [<options>]

Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
    -f, --file <file>     use given config file
    --blob <blob-id>      read config from given blob object

Action
    --get                 get value: name [value-regex]
    --get-all             get all values: key [value-regex]
    --get-regexp          get values for regexp: name-regex [value-regex]
    --get-urlmatch        get value specific for the URL: section[.var] URL
    --replace-all         replace all matching variables: name value [value_regex]
    --add                 add a new variable: name value
    --unset               remove a variable: name [value-regex]
    --unset-all           remove all matches: name [value-regex]
    --rename-section      rename section: old-name new-name
    --remove-section      remove a section: name
    -l, --list            list all
    -e, --edit            open an editor
    --get-color           find the color configured: slot [default]
    --get-colorbool       find the color setting: slot [stdout-is-tty]

Type
    --bool                value is "true" or "false"
    --int                 value is decimal number
    --bool-or-int         value is --bool or --int
    --path                value is a path (file or directory name)

Other
    -z, --null            terminate values with NUL byte
    --name-only           show variable names only
    --includes            respect include directives on lookup
```
