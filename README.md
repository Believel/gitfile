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
10. `git commit` 提交信息，并进入vm编辑界面，填写提交内容
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
