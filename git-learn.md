## 配置
1. 配置name 和 email
``` 
git config --global user.name "xxx"
git config --global user.email "xxx@xxx.xxx"
```

## 使用git
查看仓库的状态
```
git status
```
初始化仓库
```
git init
```
### 文件状态
git中的文件有两种状态：未跟踪和已跟踪。未跟踪指文件没有被git所管理，已跟踪指文件已被git管理。已跟踪的文件又有三种状态：未修改、修改和暂存。

暂存，表示文件修改已经保存，但是尚未提交到git仓库。

未修改，表示磁盘中的文件和git仓库中文件相同，没有修改。

已修改，表示磁盘中文件已被修改，和git仓库中文件不同。

可以通过git status来查看文件的状态
