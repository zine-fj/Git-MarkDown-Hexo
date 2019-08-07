## git简易版

1. 建立git仓库
``` shell
git init
```
2. 将项目所有文件添加到暂存区
``` shell
git add .
```
3. 将暂存区中文件提交到工作区
``` shell
git commit -m '备注'
```
4. 将提交的文件关联到github
``` shell
git remote add origin https://github.com/zine-fj/demo.git
（需要输入账号密码）
```
5、将文件推送到github
``` shell
git push -u origin master
有时候 -u 不行的话，换成 -f
```


## 分支问题
1、创建分支
``` shell
git branch 分支名
```
2、查看分支
``` shell
git branch
或者：git branch -a
```
3、切换分支
``` shell
git checkout 分支名
```
4、分支同时创建和切换
``` shell
git checkout -b 分支名
```
5、分支合并（此时主分支为master，要将develop合并到master）
``` shell
git merge develop
```
6、分支删除
``` shell
git checkout -d 分支名
```
7、恢复误删分支
``` shell
git log --branches="被删的分支名"
git branch develop 版本
```


















