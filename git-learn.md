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

### 未跟踪 → 暂存
```
git add <filename> 将文件切换到暂存的状态
git add * 将所有已修改（未跟踪）的文件暂存
```
### 暂存 → 未修改
```
git commit -m "xxx" 将暂存的文件存储到仓库中
git commit -a "xxx" 提交所有已修改的文件（未跟踪的文件不会提交）
```
### 未修改 → 修改
    修改代码后，文件会变为修改状态

## 常用的命令
1. 重置文件
    ```
    git restore <filename> # 恢复文件
    git restore --staged <filename> # 取消暂存状态
    ```
2. 删除文件
    ```
    git rm <filename> # 删除文件
    git rm <filename> -f # 强制删除
    ```
3. 移动文件
    ```
    git mv from to # 移动文件 重命名文件
    ```

```
git rm <filename> # 删除文件后
git restore --staged <filename> # 取消暂存状态后使用
git restore <filename> #可以恢复已删除的文件
```
