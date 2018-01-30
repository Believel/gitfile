# git 命令大全
1. `git config user.name` 查看用户名
2. `git config user.email`查看邮箱
3. `git config --global user.name "username"` 修改用户名
4. `git config --global user.email "email"` 修改邮箱地址
5. `git init` 初始化git
6. `git clone 仓储地址  [文件别名]` 从远程上克隆项目到本地，文件别名是可选的，如果不指定就是默认的项目地址名字
7. `git log` 查看所有的日志信息
8. `git status` 查看工作目录当前状态
9. `git add -A/.`提交全部
10. `git commit` 提交信息，并进入vm编辑界面，填写提交内容,需要注意：按下i(小写)是进入插入模式，这样就可以书写提交信心，然后按下esc退出回到命令模式，最后连续输入两个大写Z，就能保存退出vm编辑界面了
11. `git commit -m "commit content"` 提交信息
12. `git push origin/master` 把本地代码远程到主分支上
13. `git pull origin/master` 从远程主分支上拉取代码到本地
## 创建分支
14. `git branch one-branch1` 创建分支'one-branch1',但是不会自动切换
15. `git checkout one-branch1` 切换到 'one-branch1'分支
16. 合并上面两个命令：`git checkout -b feature` 创建并切换到feature分支
* 怎么把其他分支branch合并到master分支？
  * 1.切换到主分支master: `git checkout master`
  * 2. 合并某个分支到主干分支master: `git merge <branchName>`
17. `git branch -a` 查看所有分支信息
18. `git branch -d <branchName>` 删除分支信息
### 需要说明的地方
* `HEAD` 指向的 `branch` 不能删除。如果要删除 `HEAD` 指向的 `branch`，需要先用 `checkout` 把 `HEAD` 指向其他地方。
* 由于 `Git` 中的 `branch` 只是一个引用，所以删除 `branch` 的操作也只会删掉这个引用，并不会删除任何的 `commit`。（不过如果一个 `commit` 不在任何一个 branch 的「路径」上，或者换句话说，如果没有任何一个 `branch` 可以回溯到这条 `commit`（也许可以称为野生 commit？），那么在一定时间后，它会被 Git 的回收机制删除掉。）
* 出于安全考虑，没有被合并到 master 过的 `branch` 在删除时会失败（因为怕你误删掉「未完成」的 `branch` 啊）：
## push的本质
* 本质：把当前 `branch` 的位置（即它指向哪个 `commit`）上传到远端仓库，并把它的路径上的 commits 一并上传。
* push分支的步骤：
  * `git checkout <branchName>` 切换到分支下面
  * `git push origin <branchName>` 把当前分支上传到远端仓库中，其中`origin`是远程仓库的别名，是你在 git clone 的时候 Git 自动帮你起的；`<branchName>`是远程仓库中目标 branch 的名字；合起来意思是「我要 push 到 origin 这个仓库的 <branchName> 分支」。
## merge:合并commits
> `git pull` 的内部操作其实是把远程仓库取到本地后（使用的是 `fetch`），再用一次 `merge` 来把远端仓库的新 commits 合并到本地。

* `merge`含义：从目标 commit 和当前 commit （即 HEAD 所指向的 commit）分叉的位置起，把目标 commit 的路径上的所有 commit 的内容一并应用到当前 commit，然后自动生成一个新的 commit。
* 适用场景
  * 合并分支
  * `pull`的内部操作
* 特殊情况
  * 情况1. 遇到冲突：①解决冲突；②手动`commit`一下
    * `git merge --abort` 取消解决冲突
  * 情况2. HEAD 领先于目标 commit
    * 如果 `merge` 时的目标 `commit` 和 `HEAD` 处的 `commit` 并不存在分叉，而是 `HEAD` 领先于目标 `commit`：那么 `merge` 就没必要再创建一个新的 `commit` 来进行合并操作，因为并没有什么需要合并的。在这种情况下， Git 什么也不会做，`merge` 是一个空操作。
  * 情况3. HEAD 落后于 目标 commit——fast-forward(快速前移)
    * 如果 `HEAD` 和目标 `commit` 依然是不存在分叉，但 `HEAD` 不是领先于目标 `commit`，而是落后于目标 `commit`：那么 Git 会直接把 `HEAD`（以及它所指向的 branch，如果有的话）移动到目标 `commit`
