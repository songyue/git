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
