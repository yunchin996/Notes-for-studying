# [git](https://www.bookstack.cn/read/git-tutorial/docs-commands-git-commit.md "参考教程")


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [git](#githttpswwwbookstackcnreadgit-tutorialdocs-commands-git-commitmd-参考教程)
    - [一、基本配置](#一-基本配置)
    - [二、新建代码库](#二-新建代码库)
    - [三、克隆](#三-克隆)
    - [四、缓存区](#四-缓存区)
      - [git add](#git-add)
      - [参数](#参数)
    - [五、git commit](#五-git-commit)
      - [git commit](#git-commit)
      - [命令行参数](#命令行参数)
        - [-a](#-a)
        - [--allow-empty](#-allow-empty)
        - [--amend](#-amend)
        - [--fixup](#-fixup)
        - [-m](#-m)
        - [--squash](#-squash)
    - [六、git tag](#六-git-tag)
      - [列出已有的tag（标签）](#列出已有的tag标签)
      - [new tag](#new-tag)
      - [查看](#查看)
      - [给指定的某个commit号加tag](#给指定的某个commit号加tag)
      - [push](#push)
      - [切换tag](#切换tag)
      - [删除tag](#删除tag)
    - [七、push(推送)](#七-push推送)
    - [git remote](#git-remote)
      - [查看](#查看-1)
      - [new remote](#new-remote)
    - [pull](#pull)
    - [参考](#参考)

<!-- /code_chunk_output -->

### 一、基本配置
>用户名
```
git config --global user.name "yourname"
```
>邮箱
```
git config --global user.email "youreamil"
```
### 二、新建代码库
>在当前目录new一个Git代码库
```
git init
```
### 三、克隆
```
git clone http://git.oschina.net/yiibai/sample.git
```
### 四、缓存区
#### git add
>将指定文件放入暂存区

```
git add <file>
```
>将指定目录下所有变化的文件,放入暂存区

```
git add <directory>
```
>将当前目录下所有变化的文件，放入暂存区

```
git add .
```

#### 参数
>Git 2.0 版开始，-A参数成为默认，即git add .等同于git add -A

`-A` 或者 `--all` 参数表示追踪`所有`操作，包括新增、修改和删除
```
git add --all readme.md
```
`-u`参数表示`只`添加`暂存区`已有的文件（包括删除操作），但不添加新增的文件

```
git add -u
```

`-f`参数表示强制添加某个文件，不管`.gitignore`是否包含了这个文件
```
git add -f <fileName>
```
### 五、git commit
#### git commit
`-m`参数用于指定 `commit 信息`

```
git commit -m "message"
```
`跳过暂存区`，直接将文件从工作区提交到`仓库区`。

```
git commit <filename>  -m "message"
```
#### 命令行参数
##### -a
`-a参数`用于`先`将所有工作区的变动文件，提交到暂存区，`再`运行`git commit`则不用执行`git add .`

```
git commit -am "message"
```

##### --allow-empty
`--allow-empty`参数用于`没有提交`信息的 commit
```
git commit --allow-empty
```
##### --amend
`撤销上一次 `commit，然后生成一个`新的 commit`
```
$ git commit --amend - m "new commit message"
```

##### --fixup
当前添加的 commit 是以前某一个 commit` 的修正`。以后执行互动式的`git rebase`的时候，这两个 commit 将会`合并`成一个

```
git commit --fixup <commit>
```

##### -m
添加提交说明
```
git commit -m "message"
```

##### --squash
作用与`--fixup`类似
```
$ git commit --squash <commit>
```
###  六、git tag
#### 列出已有的tag（标签）
```
git tag
```
加上`-l`命令可以使用`通配符`来过滤tag
```
git tag -l "v3.3.*"
```
#### new tag
```
git tag v1.0
```
加上`-a`参数来创建一个`带备注的tag`，备注信息由`-m`指定
```
git tag -a tagName -m "my tag"
```
#### 查看
`git show`命令可以查看`tag的详细信息`，包括`commit号`等
```
git show tagName
```

列出tag
```
git tag --list
```
#### 给指定的某个commit号加tag
`git log`获取
```
git tag -a v1.2 9fceb02 -m "my tag"
```

#### push
推送`单个`分支
```
git push origin v1.0
```
 
推送本地所有tag
```
git push orifin --tag

```
#### 切换tag
```
git checkout v0.9
```

#### 删除tag
本地删除
```
git tag -d v0.1.2
```
远端删除
```
git push orifin :refs/tags/v0.1.2
```

### 七、push(推送)
git push `<远程主机名> <本地分支名>:<远程分支名>`
若同名则git push `<远程主机名> <本地分支名>`

```
git push origin main
```
强制推送可以使用` --force`
```
git push --force origin main
```

`--delete`删除 `origin 主机`的 master `分支`
```
git push origin :master
# 等同于
git push origin --delete master
```
不管是否存在对应的远程分支，将本地的`所有分支`都推送到远程主机
```
git push --all origin
```

git push`不会推送标签(tag)`，除非使用`--tags选项`
```
git push origin --tags
```
### git remote
#### 查看
列出已经存在的远程分支
```
git remote
origin
```
详细
```
git remote -v 
# 或者
git remote --verbose
```
#### new remote
为远程仓库添加别名
```
$ git remote add john git@github.com:johnsomeone/someproject.git
# 显示所有的远程主机
$ git remote -v
# 列出某个主机的详细信息
$ git remote show name
```
git remote命令的实质是在.git/config文件添加下面的内容
```
$ git remote add bravo ../bravo
```
```
[remote "bravo"]
    url = ../bravo/
```
### pull
`git pull <远程主机名> <远程分支名>:<本地分支名>`
取回origin`主机的`next分支，与`本地的`master分支合并
```
git pull origin next:master
```
远程分支(next)要与当前分支合并
```
git pull origin next
```
上面命令表示如同先`git fetch`，再执行`git merge`
```
$ git fetch origin
$ git merge origin/next
```

### 参考











