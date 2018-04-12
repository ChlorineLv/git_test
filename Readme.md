### Markdown语法
- 完整，简中：http://wowubuntu.com/markdown/index.html
- 简单，简中：http://wowubuntu.com/markdown/basic.html


# 初始化Git仓库
- 初始化一个Git仓库，使用 `git init` 命令;
- 第一步，使用命令 `git add file`，注意，可反复多次使用，添加多个文件;
- 第二步，使用命令 `git commit`，完成;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743256916071d599b3aed534aaab22a0db6c4e07fd0000 


# 掌握工作区的状态
- 命令 `pwd` 用于显示当前目录;
- 要随时掌握工作区的状态，使用 `git status` 命令;
- 如果 `git status` 告诉你有文件被修改过，用 `git diff` 可以查看修改内容;
- 用 `git diff HEAD -- readme.txt` 命令可以查看工作区和版本库里面最新版本的;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374829472990293f16b45df14f35b94b3e8a026220c5000 


# 版本的历史之间穿梭
- 标记HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令 `git reset --hard commit_id`;
- 穿梭前，用 `git log` 可以查看提交历史，以便确定要回退到哪个版本;
- 要重返未来，用 `git reflog` 查看命令历史，以便确定要回到未来的哪个版本;
- 再说一遍：使用命令 `git reset --hard commit_id` 跳到指定版本;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000 


# 丢弃修改
- 工作区丢弃：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令 `git checkout -- file`;
- 暂存区丢弃：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令 `git reset HEAD file` 可以把暂存区的修改撤销掉（unstage），重新放回工作区;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374831943254ee90db11b13d4ba9a73b9047f4fb968d000
 

# 删除文件
- 从版本库中删除该文件，那就用命令 `git rm` 删掉，并且 `git commit`;
- 命令 `git checkout` 其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”，但是只能恢复文件到最新版本，会丢失最近一次提交后修改的内容;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758392816224cafd33c44b4451887cc941e6716805c000 


# 克隆仓库
- 要克隆一个仓库，首先必须知道仓库的地址，然后使用 `git clone` 命令克隆;
- Git支持多种协议，包括`https`，但通过`ssh`支持的原生git协议速度最快;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375233990231ac8cf32ef1b24887a5209f83e01cb94b000 


# 创建于合并分支
- 查看分支：`git branch`;
- 创建分支：`git branch name`;
- 切换分支：`git checkout name`;
- 创建+切换分支：`git checkout -b name`;
- 合并某分支到当前分支：`git merge name`;
- 删除分支：`git branch -d name`;
 https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000 



# 分支合并
- 合并分支时，加上 `--no-ff` 参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而 `fast forward` 合并就看不出来曾经做过合并;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758410364457b9e3d821f4244beb0fd69c61a185ae0000 


# 工作中分支策略
- 在实际开发中，我们应该按照几个基本原则进行分支管理;
- 首先，`master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活;
- 你和你的小伙伴们每个人都在`dev`分支上干活，每个人都有自己的分支，时不时地往`dev`分支上合并就可以了;
- 至于`dev`分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到`master`上，在master分支发布1.0版本;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758410364457b9e3d821f4244beb0fd69c61a185ae0000 


# 工作开发
- 开发一个新`feature`，最好新建一个分支;
- 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除;
- 如果要丢弃一个没有被合并过的分支，可以通过 `git branch -D name` 强行删除;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376026233004c47f22a16d1f4fa289ce45f14bbc8f11000 


# 解决冲突
- 当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成;
- 用 `git log --graph` 命令可以看到分支合并图;
- 指令 `$ git log --graph --pretty=oneline --abbrev-commit`    //好看点的展示(?)
 https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840202368c74be33fbd884e71b570f2cc3c0d1dcf000 


# 工作现场保留
- 当手头工作没有完成时，先把工作现场 `git stash` 一下，然后去修复bug，修复后，用 `git stash list` 查看;
- 一是用 `git stash apply` 恢复，但是恢复后，stash内容并不删除，你需要用 `git stash drop`来删除;
- 另一种方式是用 `git stash pop`，恢复的同时把stash内容也删了;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000 


# 添加远程库
- 在github上"Create a new repo"，例如命名为git_test，其他保持默认设置，
-  在本地git里输入 `$ git remote add origin git@github.com:peachQAQ/git_test.git`     // 添加到本地
- 由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。
- 关联后，使用命令 `git push -u origin master` 第一次推送`master`分支的所有内容;
- 此后，每次本地提交后，只要有必要，就可以使用命令 `git push origin master` 推送最新修改;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000 
- 关于添加多个远程库和取消与远程库的链接:
<pre>
//从本地空开始添加远程的git_test，本地叫它origin
$ git remote add origin git@github.com:XXXXX/git_test.git

//查看当前本地仓库
$ git remote -v
origin  git@github.com:XXXXX/git_test.git (fetch)
origin  git@github.com:XXXXX/git_test.git (push)

//再添加一个本地名为origin1的远程库（不要在意为什么远程repo叫web-test）
$ git remote add origin1 git@github.com:XXXXX/web-test.git

//查看
$ git remote -v
origin  git@github.com:XXXXX/git_test.git (fetch)
origin  git@github.com:XXXXX/git_test.git (push)
origin1 git@github.com:XXXXX/web-test.git (fetch)
origin1 git@github.com:XXXXX/web-test.git (push)

//取消跟web-test的远程库链接
$ git remote remove origin1

//再次查看
$ git remote -v
origin  git@github.com:XXXXX/git_test.git (fetch)
origin  git@github.com:XXXXX/git_test.git (push)
</pre>


# 推送分支
- 要查看远程库的信息，用 `git remote -v`;
- 命令 `$ git push origin xxxx`     // 把xxxx推送到origin;
- 本地新建的分支如果不推送到远程，对其他人就是不可见的;
- 若推送失败，则需要先用 `git pull` 抓取远程的新提交，解决冲突后，再次推送;
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013760174128707b935b0be6fc4fc6ace66c4f15618f8d000 
- 若要推送文件夹，vscode可以直接“暂存”“提交”“推送/推送到”;
- 若是用git，则：
<pre>
//跳转到需要上传的文件夹里
//（需要在原来repo对应本地文件夹里，如原来是git_test,则现在是git_test/newfolder2)
$ cd ./newfolder2/

//添加文件到本地库里
$ git add try_folder2.txt

//然后照样commit
$ git commit -m "try using git to push new folder"
[master 81bee7e] try using git to push new folder
 1 file changed, 1 insertion(+)
 create mode 100644 newfolder2/try_folder2.txt

 //照样push到同一个远程库，
 //origin对应的是远程的repo，远程会自动在git_test里生成newfolder2文件夹
 $ git push origin master
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 396 bytes | 396.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:peachQAQ/git_test.git
   ff45d7d..81bee7e  master -> master
</pre>



# 抓取分支
- 在本地创建和远程分支对应的分支，使用 `git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致;
- 建立本地分支和远程分支的关联，使用 `git branch --set-upstream branch-name origin/branch-name`;
- 从远程抓取分支，使用 `git pull`，如果有冲突，要先处理冲突。
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013760174128707b935b0be6fc4fc6ace66c4f15618f8d000 



# 创建标签
- 命令 `git tag name`用于新建一个标签，默认为`HEAD`，也可以指定一个`commit id`;
- 命令 `git tag -a tagname -m "blablabla..."`可以指定标签信息;
- 命令 `git tag -s tagname -m "blablabla..."`可以用PGP签名标签;
- 命令 `git tag`可以查看所有标签。
 https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951758572072ce1dc172b4178b910d31bc7521ee4000 



# 操作标签
- 命令 `git push origin tagname` 可以推送一个本地标签;
- 命令 `git push origin --tags` 可以推送全部未推送过的本地标签;
- 命令 `git tag -d tagname` 可以删除一个本地标签;
- 命令 `git push origin :refs/tags/tagname` 可以删除一个远程标签。（先删除本地，再删除远端）
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951885068a0ac7d81c3a64912b35a59b58a1d926b000 



# 自定义Git
- 忽略某些文件时，需要编写`.gitignore`;
- 其中`.gitignore`文件本身要放到版本库里，并且可以对`.gitignore`做版本管理
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013758404317281e54b6f5375640abbb11e67be4cd49e0000 
- 指令 `$ git config --global alias.st status` 可以用`st`代替`status`（更多例子看见教程）
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375234012342f90be1fc4d81446c967bbdc19e7c03d3000 
