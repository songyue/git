= Your Identity

  git config --global user.name "songyue" 
  git config --global user.email songyue118*gmail.com 

= Your Editor

  git config --global core.editor vim

= Your Diff Tool

  git config --global merge.tool vimdiff

= Checking Your Setting

  git config --list

you can also check what Git thinks a specific key's value is by typing """git config {key}"""
git config user.name

对比分支 
git diff branch1 branch2 --stat // 显示出所有有差异的文件列表
git diff branch1 branch2 文件名 // 显示指定文件的详细差异
git diff branch1 branch2 // 显示出所有有差异的文件的详细差异

对比远程和本地操作相同
git diff test origin/test

==========================================

冲突操作的一些帮助命令
查看冲突文件的历史: 
    git blame 文件名
显示格式
    commit ID | 代码提交作者 | 提交时间 | 代码位于文件中的行数 | 实际代码 

git blame application/modules/Console/views/live/index.html

283a1708 (杨毅          2018-07-20 15:21:00 +0800   1) <div class="page-content">
fe92d003 (tingguang.yan 2018-09-25 10:18:19 +0800   2)     <div class="title">房间管理</div>
fe92d003 (tingguang.yan 2018-09-25 10:18:19 +0800   3)     <div class="toolbar">

可以详细的看到每一行在哪个版本修改的,然后使用 git show 版本号查看修改内容,最终确认是否为有效内容
git show 283a1708


==========================================
git 日志命令
git log [<options>] [<revision range>] [[--] <path>...] 
    --follow 文件名 ,显示单文件的日志
    -L <start>,<end>:<file>, -L :<funcname>:<file>
    -L 开始行号,结束行号:文件名 查询指定文件指定行的log
Commit Limiting
    -n <number>  限制要输出的提交数量。
    --since=<date>, --after=<date> 显示比特定日期更新的提交 
    --until=<date>, --before=<date> 显示比特定日期更早的提交    --author=<pattern> , --committer=<pattern> 指定作者
    --merges 只显示合并提交. same as --min-parents=2
    --no-merges 不显示多个父级提交,same as --max-parents=1.

EXAMPLES
git log --no-merges
    显示整个提交历史记录，但跳过任何合并

git log v2.6.12.. include/scsi drivers/scsi 
    显示自v2.6.12版以来的所有提交，其中包括chang ed include / scsi或drivers / scsi子目录中的任何文件

git log --since="2 weeks ago" -- gitk 
    最近两周内修改gitk的log. 这里的 '--' 是为了区分分支名称必须的符号

git log --name-status master..test
    显示'test'分支尚未出现在'master'分支的提交,以及每个提交修改的路径列表

git log --follow builtin/rev-list.c
    显示'builtin/rev-list.c'的提交log,包括改名之前发生的变更

git log --branches --not --remotes=origin
    显示任何本地分支中的所有提交，但不显示原始的任何远程跟踪分支中的所有提交（原始数据没有)

git log master --not --remotes=*/master
    显示本地主服务器中的所有提交，但不显示任何远程存储库主分支中的提交。

git log -p -m --first-parent
    显示包含更改差异的历史记录，但仅显示“主分支”透视图，跳过来自合并分支的提交，并显示合并引入的完整变更差异。 只有遵循严格的策略，在停留在单个集成分支上时合并所有主题分支才有意义。

git log -L '/int main/',/^}/:main.c
    显示man函数的改变历史
git log -L '/uploadAuthKey/',/}$/:application/modules/Api/controllers/Record.php
    显示uploadAuthKey 函数的修改历史
git log -3
    显示yue.song的用户日志
git log --author=yue.song
    显示yue.songyue用户的2018-11-04日的log
git log --author=yue.song --since=2018-11-06 --before=2018-11-07
       --since=<date>, --after=<date>
       --until=<date>, --before=<date>


强制合并一个未跟踪的版本库
添加一个无关的git remote时,git pull 或者mearge 时会提示 fatal:拒绝合并无关的历史,使用下面两个命令解决:
1.首先将远程仓库和本地仓库关联起来：
    git branch --set-upstream-to=origin/master master
2.然后使用git pull整合远程仓库和本地仓库，
    git pull --allow-unrelated-histories    (忽略版本不同造成的影响)
完成，问题解决


git diff中,一个tab缩进的宽度默认的是8个空格,个人习惯是4个空格,
git config --global core.pager 'less -x1,5' # 4个空格
git config --global core.pager 'less' # 默认 8个空格
