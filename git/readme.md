# [git](https://www.bookstack.cn/read/git-tutorial/docs-commands-git-commit.md "参考教程")


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [git](#githttpswwwbookstackcnreadgit-tutorialdocs-commands-git-commitmd-参考教程)
    - [一、基本配置](#一-基本配置)
    - [二、新建代码库](#二-新建代码库)
    - [三、查看目前状态](#三-查看目前状态)
    - [四、克隆](#四-克隆)
      - [https](#https)
      - [ssh](#ssh)
    - [四、缓存区](#四-缓存区)
      - [git add](#git-add)
      - [参数](#参数)
    - [五、git commit](#五-git-commit)
      - [git commit](#git-commit)
      - [命令行参数](#命令行参数)
    - [六、标签tag](#六-标签tag)
      - [本地](#本地)
      - [push](#push)
    - [七、git remote](#七-git-remote)
    - [八、合并](#八-合并)
    - [push(推送)](#push推送)
    - [参考](#参考)

<!-- /code_chunk_output -->

### 一、基本配置
>用户名、Email
```bash
git config --global user.name "yourname"
git config --global user.email "youreamil"
```
### 二、新建代码库
>在当前目录new一个Git代码库并生成一个 .git 目录。
```bash
git init
```

### 三、查看目前状态
```bash
git status
```

### 四、克隆
#### https
`git clone`命令用于克隆远程`分支`
```bash
git clone http://git.oschina.net/yiibai/sample.git
```

#### ssh
1.ssh
```bash
ssh-keygen  –t rsa  –C"yunchin.white@qq.com"
```
2.查看公钥
```bash
cat ~/.ssh/id_rsa.pub
```
3.copy to github
```
个人设置」->「安全设置」->「SSH公钥」->「添加公钥」
```
4.clone
```bash
 git clone "ssh网址"
```

### 四、缓存区
#### git add
>将指定文件放入暂存区

```bash
git add <file>
```
>将指定目录下所有变化的文件,放入暂存区

```bash
git add <directory>
```
>将当前目录下所有变化的文件，放入暂存区:palm_tree:
```bash
git add . 
```

#### 参数
Git 2.0 版开始，-A参数成为默认，即`git add .`等同于`git add -A`

|参数|解释|
|:---|:---|
|`-A` 或者 `--all`| 表示追踪`所有`操作，包括新增、修改和删除|
|`-u`|`只`添加`暂存区`已有的文件（包括删除操作），但不添加新增的文件|
|`-f`|参数表示强制添加某个文件，不管`.gitignore`是否包含了这个文件|


### 五、git commit
#### git commit
`-m`参数用于指定 `commit 信息`:palm_tree:

```bash
git commit -m "message"
```
`跳过暂存区`，直接将文件从工作区提交到`仓库区`。

```bash
git commit <filename>  -m "message"
```

查看提交commit信息
```bash
git log
```
#### 命令行参数

|参数|解释|
|:---|:---|
|-a|`先`将所有工作区的变动文件，提交到暂存区，`再`运行`git commit`则不用执行`git add .`|
|allow-empty|用于`没有提交`信息的 commit|
|--amend|`撤销上一次 `commit，然后生成一个`新的 commit`|
|--fixup|当前添加的 commit 是以前某一个 commit` 的修正`。以后执行互动式的`git rebase`的时候，这两个 commit 将会`合并`成一个|
|-m|添加提交说明|
|--squash|作用与`--fixup`类似|

###  六、标签tag
#### 本地
列出标签（可带上`-l `或` --list`加`*`通配符）
```bash
git tag
```
`-a`创建`附注标签`
```bash
git tag -a v1.4 -m "my version 1.4"
```
`轻量标签`（无-a、-s 或 -m ）
```bash
git tag v1.4
```
标签`详情`
```bash
git show v1.4
```
指定版本（验和的`前几位数字`即可）
```bash
git tag -a v1.2 9fceb02 -m "my tag"
```

#### push
共享标签
```bash
 git push origin v1.5   //单个tag
 git push origin --tags //多个
```
`删除`标签
```bash
git tag -d v1.4                //删除本地

git push origin :refs/tags/v1.4  //同步
或
git push origin --delete <tagname>

```
检出标签(分支)
```bash
git push origin --delete <tagname>
```
### 七、git remote
添加远程地址
```bash
git remote add origin "https://..."
```
查看本地添加了哪些远程地址
```bash
git remote -v
```
删除
```bash
git remote rm <远程源>
```

### 八、合并
```bash
//取回origin`主机的`next分支，与`本地的`master分支合并

git pull <远程主机名> <远程分支名>:<本地分支名>
git pull origin next:master

//远程分支(next)要与`当前分支`合并
git pull origin next
```
上面命令表示如同先`git fetch`，再执行`git merge`
```bash
$ git fetch origin
$ git merge origin/next
```

### push(推送)
git push `<远程主机名> <本地分支名>:<远程分支名>`
若同名则git push `<远程主机名> <本地分支名>`

```bash
git push origin main
```
强制推送可以使用` --force`
```bash
git push --force origin main
```

`--delete`删除 `origin 主机`的 master `分支`
```bash
git push origin :master
# 等同于
git push origin --delete master
```
不管是否存在对应的远程分支，将本地的`所有分支`都推送到远程主机
```bash
git push --all origin
```

git push`不会推送标签(tag)`，除非使用`--tags选项`
```bash
git push origin --tags
```

### 参考
[git的操作](https://www.bookstack.cn/read/git-tutorial/docs-operations.md)

[git官方](https://www.git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE)
