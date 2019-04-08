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


