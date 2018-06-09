## hexo更换电脑时同步问题
当你在公司的一台电脑上成功部署完hexo并且发表一篇博客时，别着急激动！有没有想过回家后还想用hexo怎么办呢？

思路：在生成的已经推到github上的hexo静态代码上简历一个分支，利用这个分支来管理自己的hexo源文件

具体操作：
1. 克隆github上面生成的静态文件到本地
``` powershell
git clone https://github.com/zine-fj/zine-fj.github.io.git
```
2. 把克隆到本地的文件除了git的文件都删掉，找不到git的文件的话就都删了吧。不要用 ``hexo init`` 初始化。
3. 将之前使用hexo写博客时的整个目录(所有文件)搬过来。把该忽略的文件忽略
``` powershell
touch .gitignore
```
4. 创建一个叫hexo的分支
``` powershell
git checkout -b hexo
```
5. 将复制过来的文件推送到github
``` powershell
git add .
git commit -m "新建分支"
git remote add origin https://github.com/zine-fj/zine-fj.github.io.git
git push -u origin hexo
```
6. 以后在其他电脑上用hexo写博客，就可以直接将创建的分支克隆下来，在用 ``yarn`` 安装依赖就可以了
``` powershell
git clone -b hexo https://github.com/zine-fj/zine-fj.github.io.git hexo
```
7. 做完之后，每次写完博客发布之后，不要忘了还要 ``git push`` 把源文件推到分支上

注意：如果用 ``hexo s`` 查看 [localhost:4000](localhost:4000) 是空白的话，可能是因为没有获取到主题(主题在 ``themes`` 文件夹中)。
