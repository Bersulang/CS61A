# Git Use Help Doc :book:
## 创建版本库 :smile:
- 打开Git Bash 并且创建一个文件夹，进入该文件夹
- 在Git Bash中输入 `git init` 这可以让该目录变成Git可以管理的仓库：
```
$ git init  
Initialized empty Git repository in C:/Users/Famig/Git_store/.git/
```
> 此时可以用 `ls -ah` 可以查看多出来的隐藏目录（这个名为 `.git` 的隐藏目录就是我们的版本库）

- 然后我们可以在这个目录里面创建一个文件例如我有一个名为 `test.py` 的文件，现在通过 `git add test.py` 把文件添加到缓存区，这时如果没有显示任何东西，那这就对了，接着我们使用 `git commit -m "this is a test to commit"` 命令将文件提交到仓库：
```
$ git commit -m "this is a test to commit"
[master (root-commit) ae8f98c] this is a test to commit
 1 file changed, 2 insertions(+)
 create mode 100644 test.py
```
> 这里 `git commit` 就是提交命令，而 `-m` 和后面的内容是这次提交的备注，方便你以后查看和管理版本

    在git commit 后面添加--amend参数可以对最近一次的提交进行修改而不产生新的提交
### 总结一下：
1. 使用 `git init` 命令初始化一个git仓库
2. 使用 `git add <file>` 命令来将文件添加到暂存区
3. 使用 `git commit` 命令将暂存区的所有文件提交到git仓库
> `git add` 命令可以一次将多个文件添加到暂存区，只需要文件名之间间隔一个空格，而不在暂存区的文件不会被 `git commit` 命令提交到git仓库

## 版本管理
- `git status` 可以帮助我们时刻查看当前仓库的状态：
```
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .test.py.un~
        .test.txt.un~
        test.txt

nothing added to commit but untracked files present (use "git add" to track)
```

- `git diff <file>` 可以帮助我们查看修改同一文件之后两者的版本差异：
```
$ git diff test.py
diff --git a/test.py b/test.py
index 53aa9ca..e55b0a4 100644
--- a/test.py
+++ b/test.py
@@ -1,2 +1,3 @@
 say="hello world"
 print(say)
+print(!)
```
> 如果你的修改未提交那么可以使用 `git diff HEAD --<file>` 来查看版本库里的文件和工作区里的该文件之间的差异

- `git log` 可以查看提交版本的历史记录：
```
$ git log
commit 7375023625471c9ef5fdd4ed18c8dd614df4708c (HEAD -> master)
Author: LazyPig <bersulang0627@gmail.com>
Date:   Sun Nov 10 16:01:39 2024 +0800

    add a print

commit ae8f98c3f02fcd6c6ed834d74a142d804ff47b64
Author: LazyPig <bersulang0627@gmail.com>
Date:   Sun Nov 10 15:35:40 2024 +0800

    this is a test to commit
```
还可以使用参数例如：`git log --pretty=oneline` 来简化输出：
```
$ git log --pretty=oneline
7375023625471c9ef5fdd4ed18c8dd614df4708c (HEAD -> master) add a print
ae8f98c3f02fcd6c6ed834d74a142d804ff47b64 this is a test to commit
```
> 可以注意到这里有个 `HEAD->master` 意思就是当前的版本是这个分支的这个版本

- `git reflog` 可以查看你使用的历史命令：
```
$ git reflog
ae8f98c (HEAD -> master) HEAD@{0}: reset: moving to HEAD^
7375023 HEAD@{1}: commit: add a print
ae8f98c (HEAD -> master) HEAD@{2}: commit (initial): this is a test to commit
```
- `git reset` 命令可以进行版本回退:
```
$ git reset --hard HEAD^
HEAD is now at ae8f98c this is a test to commit
```
> `--hard` 参数是指回退到上个版本的已提交状态， `--soft` 参数会回退到上个版本的未提交状态， `--mixed` 参数会回退到上个版本已添加但是未提交的状态(默认值为mixed)，`HEAD^`也可以换成指定的版本号例如 `ae8f98`, `git reset HEAD <file>` 可以把该文件从暂存区的修改撤销

    需要注意的是相较于reset，revert更适合在协作开发时使用，而reset更适合在本地进行版本回退

- `git checkout -- <file>` 可以将文件回退到上一次 `git add` 或 `git commit` 的状态：

- 在这里拓展一下 `git checkout` 这个命令：
  1. `git checkout <num>` 可以将HEAD指针移到 `num` 处的提交记录，这里 `num` 可以使用绝对引用的哈希值，也可以使用相对引用
  2. `git checkout -b <branch>` 可以快速创建一个分支并将HEAD指针指向该分支
  3. `git checkout -b <main> <o/main>` 可以将两个分支进行跟踪关联，后面的为你远程仓库的分支名
- `git rm <file>` 可以删除版本库中的文件：
```
$ git rm test.py
rm 'test.py'

$ git commit -m "delete"
[master a00becf] delete
 1 file changed, 2 deletions(-)
 delete mode 100644 test.py
```
## 远程仓库的管理
- `ssh-keygen -t rsa -C "Youremail@example.com"`用于创建你的ssh密钥，带 `.pub` 的公钥可以公开使用，另一个私钥需要防止泄露

- `git remote add origin "你的GitHub仓库地址"` 可以将你本地的Git仓库与Github上的远程仓库进行关联，这里 `origin` 是远程库的名字，也可以换成别的

- `git push -u origin master` 可以把本地库的所有内容推送到远程库
> 后续想要继续提交只需要 `git push origin master` 命令即可

- 在这里拓展一下 `git push` 这个命令:
  1. `git push` 可以将本地仓库更新的提交推送至远程仓库
  2. `git push origin <branch>:<o/branch>` 则为将本地的 `branch` 分支提交更新推送至远程仓库的 `o/branch` 分支

- `git remote rm <name>` 可以取消与远程库的关联
>  `git remote` 可以查看远程库的名字，`git remote -v` 可以查看远程库详细信息

- `git clone "你的GitHub仓库地址"` 可以从Github克隆远程库到你的本地

- `git branch` 可以查看当前所有分支
> `git branch -d <name>` 可以删除分支, `git branch -D <name>` 可以强行删除分支

- 在这里拓展一下 `git branch` 这个命令:
  1. `git branch <name>` 可以创建分支
  2. `git branch -f <name> <target>` 可以将 `name` 指针移到 `target` 处的提交记录
  3. `git branch -u <o/branch> <branch>` 可以让本地的 `branch` 分支跟踪关联远程仓库的 `o/branch` 分支

- `git stash` 可以把当前工作全部打包储存起来，此时你可以去处理别的问题
> 使用 `git stash apply` 可以恢复内容，但是恢复后该stash内容并不会删除(apply后面可以加参数恢复指定的stash)，需要使用 `git stash drop` 来删除，使用 `git stash list` 可以查看打包记录，使用 `git stash pop` 在回复的同时也会删除该stash

- `git merge <branch>` 可以帮助你进行分支合并，它会将 `branch` 分支合并到当前HEAD所指分支

- `git rebase` 作用和 `git merge` 差不多，但是它会更改提交历史，这样带来的好处就是会让提交记录跟线性，说简单点就是更好看了
> 在这里拓展一下：
-   `git rebase -i <target>` 可以打开一个UI界面，此时你可以对 `target` 之后的提交进行选择和排序

- `git cherry-pick <name>` 你可以任选多项提交记录放在HEAD当前所指的提交记录后，多个 `name` 间只需要用空格隔开

- `git tag <tag_name> <name>` 可以为 `name` 这个提交记录打上 `tag_name` 标签

- `git fetch` 命令不会改变你本地代码库的状态，也不会对本地文件进行修改

- `git pull` 就是 `git fetch` 和 `git merge` 的结合
> `git pull --rebase` 就是 `git fetch` 和 `git rebase` 的结合