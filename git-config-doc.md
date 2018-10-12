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
