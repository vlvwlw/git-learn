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
### 分支
git 在存储文件时，每一次代码代码的提交都会创建一个与之对应的节点，git 就是通过一个一个的节点来记录代码的状态的。节点会构成一个树状结构，树状结构就意味着这个树会存在分支，默认情况下仓库只有一个分支，命名为 master。在使用 git 时，可以创建多个分支，分支与分支之间相互独立，在一个分支上修改代码不会影响其他的分支。
```
git branch # 查看当前分支
git branch <branch name> # 创建新的分支
git branch -d <branch name> # 删除分支
git switch <branch name> # 切换分支
git switch -c <branch name> # 创建并切换分支
git merge <branch name> # 和并分支
```

### 变基（rebase）
在开发中除了通过 merge 来合并分支外，还可以通过变基来完成分支的合并。

我们通过 merge 合并分支时，在提交记录中会将所有的分支创建和分支合并的过程全部都显示出来，这样当项目比较复杂，开发过程比较波折时，我必须要反复的创建、合并、删除分支。这样一来将会使得我们代码的提交记录变得极为混乱。

原理（变基时发生了什么）：

1. 当我们发起变基时，git 会首先找到两条分支的最近的共同祖先
2. 对比当前分支相对于祖先的历史提交，并且将它们提取出来存储到一个临时文件中
3. 将当前部分指向目标的基底
4. 以当前基底开始，重新执行历史操作

变基和 merge 对于合并分支来说最终的结果是一样的！但是变基会使得代码的提交记录更整洁更清晰！注意！大部分情况下合并和变基是可以互换的，但是如果分支已经提交给了远程仓库，那么这时尽量不要变基。