[toc]

# git使用

## 安装

从网上下安装包

装好有个Git Bash,Git GUI

主要用Bash命令行



git config --global user.name "我的用户名"

git config --global user.email "我的邮箱，随便写，它不验证的"

## 使用

### 创建版本库

先进要创建版本库的文件夹

新建用mkdir NewFolder

在这个文件夹里 git init

出一个.git文件夹

### 进缓存区和提交

此目录下，我新建了一个demo.txt

(创建文本文件，文件名就不要自己再打一个.txt了，会重的)

```
git add demo.txt//是把这个文件加入暂存区了
git commit -m 'demo提交'//这个commit是把所有暂存区的文件，一次性全提交进仓库，-m只是提交的注释
```

此时，使用git status 会显示，没有文件可提交

然后，我改掉了demo.txt，并且**没有**输入任何命令

再用一次git status ,改过的文件会标红

```
git diff demo.txt//看有什么不一样
```

然后再次**先add,再commit**把改后的文件提交进仓库

**注意，-m和之后的message必须要写，不写直接git commit ，它会进编译器逼着写message 的**

add了没commit,此时使用git status ，文件是被标绿的。

### 回退（除去上次的修改）

```
git log//看提交的日志，会显示每一次的提交
git rest --hard HEAD^//是回退一次，此时我的demo.txt只剩下11111和2222了，回退两次是HEAD^^，回退一百次是HEAD~100
看txt内容用cat demo.txt

```

回退之后用log就少一条记录。

### 反回退（把修改再还回来）

刚才git log 不是列出来所有add commit的记录嘛，一长串的乱码就是一次记录的版本号，

如果我想要3333再回来，

就先找到有3333的那个版本的长串版本号复制，

用git rest --hard +版本号

如果bash重开过找不到版本号了，就git reflog，仍然会出版本号（较短），继续上文那么用。

### 工作区

正常的电脑上的目录

### 版本库

.git这个文件夹下，是版本库，里面包括暂存区（但是没有专门文件夹）

## 连github

ssh-keygen -t rsa –C “youremail@example.com”

此时，用户文件夹下出.ssh文件夹，里面是id_rsa(私钥，不可以泄露)，id_ras.pub(公钥，随便给)

开github自己主页，setting-SSH-add ssh

然后把公钥内容粘进去（用记事本可以开）

## 推拉文件

### 一个全新的仓库连接

git remote add origingit@github.com:DayDreamer9090/test.git

之后再改

add commit之后

```
git push origin master
```

别的参数不用加，远程就能自己改

!!!注意，这个只对全新的github仓库能用，已经有文件的会报错

