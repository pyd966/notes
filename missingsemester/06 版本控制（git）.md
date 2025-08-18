tree，文件夹；
blob，文件；
使用 DAG 来建模历史快照，你可以 fork 不同的 branches，最终可以合并起来。
`git init` 初始化
`git help [command]`
`git status`
`git add [file]` 开始 track 一个文件
`git commit` 提交
`git log` 显示提交记录
`git log --all --graph --decorate` 以图的方式展示
`git checkout [hash]` 可以切换到之前的某个 commit，会改变你当前的文件
`git checkout [file]` 将 file 修改为 HEAD 版本的状态
`git diff [file]` 显示跟 HEAD 的差异
`git branch` 查看当前所有 branch
`git branch [name]` 新建一个 branch，指向 HEAD
`git checkout [branchname]` 切换到 branchname
`git merge [branchname]`
`git merge --continue` 解决冲突之后继续合并
`git remote` 列出远程仓库
`git remote add [name] [url]`
`git push [name] [local branch]:[remote branch]`
`git clone [url] [folder]`
`git clone --shallow` 只克隆最新版本
`git fetch [remotename]`