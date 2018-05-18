## 我们的技术栈 - Git

 `付杰`



## GIT
分布式的版本控制系统


### 源码管理 Source Control
等同于 `版本控制`、`Version control`、`Revision control`
对源代码的版本的管理：

- 追踪变更：谁，在什么时候，增删改了什么
- 版本控制：不同版本间差异、版本发布
- 权限控制：谁可读什么、谁可写什么
- ...


### 发展历程
- 本地 `Local only`
- CS模式 `Client-server`
  - `CVS 1986`、`ClearCase* 1992`、`Subversion 2000`
- 分布式 `Distributed`
  - `BitKeeper 2000`、`Git 2005`、`Visual Studio Team Services* 2010`


### CVS
- 优点：集中化存储、简单、性能优异
- 缺点：无分支、无全局版本号、提交不保证原子性


### SVN
- 优点：集中化存储、简单、分支、提交原子性、递增的提交号
- 缺点：
  - 重命名极易造成冲突
  - 无法删除历史
  - 分支代价高昂（服务端）
  - 联网


### GIT历史

- 1991 `Linus`创建了`Linux`
- 2002 `diff`方式管理源码
- 2002  授权`Linux`社区免费使用`BitKeeper`
- 2005  收回授权
- 2周   `Linus`参考`BitKeeper`，用C写出了`Git`
- 1月   `Linux`源码迁移至`Git`
- 2008  `GitHub`网站上线

注意：此处特指 `Linux Kernel`

- 1991年的linux-0.0.1.tar.gz文件为71K、解压后230K；
- 2002年的linux-2.4.20.tar.gz文件为32M；
- 参见：https://mirrors.kernel.org/


### Git的安装

![Git for Windows 安装](git-setup.png)

***尝试：*** 好用的Linux Shell，[**MinGW** *| Minimalist GNU for Windows*](http://mingw.org/)

``` shell
# Windows
echo %PATH%
mkdir a
dir
rd /S a
cls
```

``` shell
# Linux
echo $PATH
mkdir b
ls
rm -r b
clean

which rm
ps
vi
```


### Git核心概念

- 文件
![git-files-1](git-files-1.jpg)

![git-files-2](git-files-2.jpg)

- 3个区域：工作区、暂存区 `Index` / `Stage `、本地仓库
![git-area](git-area.png)

- 3个状态：已修改 `modified`、已暂存 `staged` 、已提交 `committed`
![git-area](git-area.jpg)

- 分支： `master` 、 `HEAD`
  Git 中的分支实际上仅是一个包含所指对象校验和（40 个字符长度 SHA-1 字串）的文件，所以创建和销毁一个分支就变得非常廉价。说白了，新建一个分支就是向一个文件写入 41 个字节（外加一个换行符）那么简单，当然也就很快了。

- 单个提交对象
![git-branch-1.png](git-branch-1.png)

- 多个提交对象
![git-branch-2.png](git-branch-2.png)

- 创建新分支
![git-branch-3.png](git-branch-3.png)
``` shell
$ git branch testing
```

- 检出新分支
![git-branch-4.png](git-branch-4.png)
``` shell
$ git checkout testing
```

- 提交修改
![git-branch-5.png](git-branch-5.png)
``` shell
$ vim test.rb
$ git commit -a -m 'made a change'
```

- 检出分支master
![git-branch-6.png](git-branch-6.png)
``` shell
$ git checkout master
```

- 提交修改
![git-branch-7.png](git-branch-7.png)
``` shell
$ vim test.rb
$ git commit -a -m 'made other changes'
```

- Git Flow
![git-flow](git-flow.jpg)


### Git常规操作

#### git help

```` shell
$ git
$ git help config
````


#### git config

``` shell
$ git config --global user.name "Lin Guo"
$ git config --global user.email linguo@karrytech.com

# 别名
$ git config --global alias.co checkout
$ git config --global alias.ci commit

# 查看设置
$ git config --global --list

# 查看全局配置文件
$ cat $USERPROFILE/.gitconfig

# 查看仓库配置文件
$ cat .git/config
```


#### git init

``` shell
# 初始化本地仓库
$ git init
```


#### git clone

``` shell
# 克隆远程仓库
$ git clone https://github.com/hakimel/reveal.js.git

$ git clone https://github.com/hakimel/reveal.js.git my-reveal
```

- 增加远程仓库 ***origin***
- 增加本地*master*分支与远程*master*分支的跟踪


#### git status

````shell
$ git status
````

- 工作区：所在分支、未暂存内容
- 暂存区：已暂存内容


#### git add / git stage

```shell
# 加入到暂存区
git add README.txt
git stage README.txt
```


#### git commit

``` shell
# 提交至本地仓库
git commit -m "Add README.txt"
```


#### git log

``` shell
# 查看日志
git log

git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```


#### git branch

``` shell
# 创建分支
$ git branch feature-1

# 从特定Commit创建分支
$ git branch feature-1 23d9effe

# 删除
$ git branch -d feature-1

# 强行删除
$ git branch -D feature-1

# 重命名
$ git branch -m feature-1 develop-1

# 查看本地分支列表
$ git branch

# 查看远程分支列表
$ git branch -r

# 查看所有分支
$ git branch -a
```


#### git checkout

````shell
# 检出分支
$ git checkout feature-1

# 检出文件
$ git checkout -- README.md

# 检出远程分支
$ git checkout develop origin/develop
````


#### git remote

``` shell
# 查看远程仓库
$ git remote
$ git remote -v

# 查看远程仓库信息
$ git remote show origin

# 增加远程仓库
$ git remote add test4 file:///C:\Users\colin\Desktop\test4

# 移除远程仓库
$ git remote remove test4
```


#### git merge

![git-merge-1.png](git-merge-1.png)


![git-merge-2.png](git-merge-2.png)

``` shell
$ git checkout master
$ git merge experiment
```

两个分支最新的快照（C3 和 C4）以及共同祖先（C2）进行三方合并。
**注意：** 会产生一个新的提交对象（C5）。


#### git rebase

![git-rebase-1.png](git-rebase-1.png)

``` shell
$ git checkout experiment
$ git rebase master
```

将当前分支（experiment）的后续提交，在基底分支（master）重放，最后会生成一个新的合并提交对象（C3'）。从而改写 experiment 的提交历史，使它成为 master 分支的直接下游。

![git-rebase-2.png](git-rebase-2.png)

**目的：**把解决分支补丁同最新主干代码之间的冲突，由提交补丁的人来解决。


#### 合并 & 变基

- 合并是把最终结果合在一起
- 变基是按照每行的修改次序重演一遍修改
- 都会得到相同的快照内容，但提交历史不同


#### git fetch &amp; git pull

``` shell
# 拉取远程仓库的更新，不做自动合并
$ git fetch origin

# 拉取远程仓库的更新，对当前分支做自动合并
$ git pull
```

*git pull = git fetch + git merge*


#### git push

``` shell
# 将本地分支feature-1推送到远程仓库origin
$ git push origin feature-1

# 推送并指定远程分支名
$ git push origin feature-1:KTIP-001

# 推送空分支，等同于删除远程分支
$ git push --delete origin :KTIP-001
```


#### git tag

``` shell
# 增加轻量标签
$ git tag v1.0

# 增加附注标签
$ git tag -a v1.0 -m 'Create version 1.0'

# 查看标签
$ git tag

# 查看标签详情
$ git show v1.0
```

***注意：*** `git tag` 与 `git branch` 的区别
***注意：*** `detached HEAD`


#### 撤销修改

``` shell
# 已修改，丢弃工作区
$ git checkout -- readme.txt

# 已暂存，丢弃暂存区，修改回到工作区
$ git reset HEAD readme.txt

# 已提交，让HEAD指向旧版本，更新工作区
$ git reset --hard HEAD~1
```


#### .gitignore

***推荐：*** 辅助生成 `.gitignore` 的工具网站

[Create .gitignore](https://www.gitignore.io/)

[A collection of .gitignore templates](https://www.gitignore.io/)



### Git实践

````shell
# 初始化
$ mkdir test && cd test
$ git init

# 分支master
$ echo '' > master.txt
$ git add master.txt
$ git commit -m 'Add master.txt'
$ git log

# 分支feature-1
$ git branch feature-1
$ echo '' > feature-1.txt
$ git add feature-1.txt
$ git commit -m 'Add feature-1.txt'
$ git log

# 分支feature-2
$ git branch feature-2
$ echo '' > feature-2.txt
$ git add feature-2.txt
$ git commit -m 'Add feature-2.txt'
$ git log

# 分支feature-1合并至master
$ git checkout master
$ git merge feature-1
$ git log
````


***尝试：*** 找到 `commit` 对象
***尝试：*** 手工造一个假分支，`.git\refs\heads`
***尝试：*** 当 工作区、暂存区 都有未Commit的修改时，切换到其他分支，再Commit


### EGit实践

***尝试：*** 找到 `origin`
***尝试：*** 添加多个 `remote`，本地仓库、远程仓库，并推送


### EGit最佳实践

- pull之前：请确认已commit
- pull之前：请确认已设置跟踪待合并的远程分支、勾选Rebase
- push之后：请确认在gitlab上创建了Merge Request
- push之后：请确认已告知Code Review人员


### Git不适合于什么场景

- 二进制文件，比如Word、Excel、PPT。推荐SVN、Google Docs、 .doc转.md


### 更多用法

#### 在GitHub建立博客

``` shell
$ git clone https://github.com/username/username.github.io
$ cd username.github.io
$ echo "Hello World" > index.html
$ git add --all
$ git commit -m "Initial commit"
$ git push -u origin master
```

**提问：**如何存储动态数据？


#### 在GitBook上写书

**GitBook**是一个基于Git、Markdown进行书籍创作的平台，可以托管、在线编辑、团队协作、售卖等。

[例：GitBook简明教程](http://www.chengweiyang.cn/gitbook/introduction/README.html#)


#### 基于Git的分布式配置中心

**Spring Cloud Config** 是一个分布式配置中心，可以在Git上存储配置信息。

![git-spring-cloud-config.png](git-spring-cloud-config.png)

**pom.xml**

``` xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-config-server</artifactId>
</dependency>
```

**Application.java**

``` java
@EnableConfigServer
@SpringBootApplication
public class ConfigServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(ConfigServerApplication.class, args);
    }
}
```

**application.properties**

``` properties
spring.cloud.config.server.git.uri=https://github.com/username/xxx-project/
spring.cloud.config.server.git.search-paths=/config/
spring.cloud.config.label=master
#spring.cloud.config.server.git.username=username
#spring.cloud.config.server.git.password=password
```


#### 基于Git的NoSQL数据库

- 基于JGit
- 基于命令行


### 文章
[1]: (https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) "Git教程-廖雪峰"
[2]: https://zhuanlan.zhihu.com/p/22750675 "Git核心概念"
[3]: https://git-scm.com/book/zh/v2 "Pro Git - 2nd Editor (2014)"
[4]: http://www.chengweiyang.cn/gitbook/introduction/README.html# "GitBook简明教程"
[5]: http://wiki.eclipse.org/EGit/User_Guide "EGit User Guide"
[6]: https://www.kenneth-truyers.net/2016/10/13/git-nosql-database/ "Git as a NoSQL database"
[7]: http://www.ituring.com.cn/article/56870 "基于Git的源码管理模型"
[8]: https://github.com/vigente/gerardus/wiki/Integrate-git-diffs-with-word-docx-files "Integrate git diffs with word docx files"
[9]: https://www.jianshu.com/p/1e402922ee32 "Markdown 入门指南"

### 官网
[1]: https://gitforwindows.org/	"git for windows"
[2]: http://www.eclipse.org/egit/ "EGit"
[3]: https://pages.github.com/ "GitHub Pages"
[4]: https://www.gitbook.com/ "GitBook"
[5]: https://mirrors.kernel.org/ "Linux Kernel"
[6]: https://cloud.spring.io/spring-cloud-config/ "Spring Cloud Config"
[7]: https://www.gitignore.io/ "Create useful .gitignore Files For Your Projects"
[8]: http://mingw.org/ "MinGW | Minimalist GNU for Windows"
