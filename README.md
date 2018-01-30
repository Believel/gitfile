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
