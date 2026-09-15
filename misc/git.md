
学习 git，应该把 git 的底层原理跟 git 提供的命令交互分开来学。如果一开始就看 git 那一大堆（组织得并不好）的命令，是学不会 git 的。

## 底层原理

git 是一个版本控制（version control, VC）工具。此前的 VC 大多都是中心化的，需要跟服务器通讯，并且它们版本控制的方式通常是**记录差异**。

而 git 不同，git 是一个分布式版本控制工具，每个人都在本地保存一份完整的历史记录，并且 git 保存版本的方式是**完整保存快照**。

git 底层就这么几个概念：blob, tree, commit。

- blob 就是文件，也就是一串字节流。
- tree 是文件夹，或者更严谨来说，tree 是一个 `map<string, tree|blob>`，把名字映射到 tree 或者 blob。
- commit 就是一次快照，它通常由一个 tree 以及一些 metadata（作者、时间等等）组成。

所有 commit 历史组成一张 DAG，代表它们的开发关系。

至于所谓的分支名，其实只是一个指针，指向某一个 commit 罢了。

以上就是 git 的所有底层原理。在学习 git 时我们还会碰到这样几个概念，它们属于实现细节，但是经常容易混淆，所以我们也提一下：

- workplace，就是当前在电脑上，你能看到的工作区域，你可以在这里任意修改。
- staging area，暂存区，其实就是对某一时刻 workplace 的快照，你可以把它想象成下一次 commit 的雏形，在这里你可以决定哪些文件要被 git 追踪、哪些修改需要被提交到下一次 commit 中
- history，就是所有的 commit 历史。

git 被设计为不可变的，也就是说一切你 commit 过的东西，在 git 中都很难被修改（不是不行）。然而，在 workplace, staging area 的内容可能会丢失。

## 命令

太基础的我们就不说了，这毕竟是一份学习笔记，我把有必要的拿出来讲一下。

### diff

`git diff` 默认会输出 workplace 跟 staging area 之间的 diff，而 `git diff --cached` 或者 `git diff --staged` 会输出 staging area 跟 last commit 之间 diff。

### rm

`git rm` 可以把文件删除、并且让 git 不再追踪。其实相当于你手动删除然后进行一次 `git add`。

`git rm --cached` 可以把文件让 git 不再追踪。

### mv

`git mv` 可以重命名。

### commit

`git commit -a` 可以 add 所有已经被追踪的文件。

`git commit --amend` 允许你修改最后一次 commit（其实并没有修改，那个 commit 还在，只是被覆盖了）。

### reset

应该有很多用途，之后来补充。

`git reset HEAD <file>` 可以把文件从 staging area 移出。

### checkout

也有很多用途。

`git checkout -- <file>` 会用把文件恢复成最后一次 commit 的样子。

### remote

远程仓库相关。

`git remote -v` 查看。

`git remote show <remote>`

`git remote add <name> <url>`

`git remote rename <old> <new>`

`git remote remove <remote>`

`git fetch <remote>` 从 remote 处更新数据，这不会进行任何修改，只是同步数据。

`git push <remote> <branch>` 把自己的分支推送到 remote。其实可以写 `git push <remote> <branch1>:<branch2>` 代表把本地的 

### tag

重要的 commit 可以打标签，分为轻量标签（lightweight）跟附注标签（annotated）两类。轻量标签更像是一个不会改变的 branch，而附注标签是一个 git 数据库中的对象。

`git tag` 列出

`git tag -a <tag> -m <comments>` 创建附注标签。

`git show <tag>` 查看 tag 

`git tag <tag>` 创建轻量标签

`git tag -a <tag> <commit>` 也可以给过去的打标签

默认情况下，push 不会把标签也传过去，必须显式推送，比如 `git push origin <tagname>`，也可以用 `git push origin --tags` 把所有标签都推送过去。

`git tag -d <tag>` 删除本地的 tag，但是不会更新到 remote。可以使用 `git push <remote> :refs/tags/<tag>` 来更新，这个含义是把冒号前面的空值推送到标签名来删除。另外也可以 `git push origin --delete <tag>`

## alias

`git config --global alias.<alias> <something>` 可以设置别名，比如 `git config --global alias.ci commit` 可以让我们输入 `git ci`。

## branch

就是一个标签类似状物。

`git branch` 列出所有 branch，也有 `git branch -v`，此外 `--merge`, `--no-merged` 可以显示已合并/未合并到当前分支的分支。

`git branch <name>` 在当前位置创建一个分支

`git checkout <name>` 切换分支

`git checkout -b <name>` 创建并切换

`git branch -d <name>` 删除

`git merge <name>` 跟某个东西合并，如果有冲突需要修改，然后再次 commit

## 跟踪分支

`git checkout -b <branch> <remote>/<branch>` 创建，也可以用 `git checkout --track <remote>/<branch>`。如果你在这个分支上 pull，它就会自动去抓取、合并。

`git branch -u <remote>/<branch>` 设置当前分支去追踪。

`git branch -vv` 可以列出本地分支以及远程追踪的分支。

`git push origin --delete <name>` 在远程服务器上删除一个分支。

## rebase

像是提取出所有修改，然后在另外一个的基础上重新应用。

`git rebase <branch>` 可以把当前分支变基到某个分支。

当然也可以 `git rebase <branch1> <branch2>` 就是把 2 的修改变基到 1 上。

