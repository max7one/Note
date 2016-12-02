## 初始设置

#### [github help](https://help.github.com/)

    git config --global user.name "Your Name"
    git config --global user.email "email@example.com"
    设置用户名和邮箱

    git config --global core.quotepath false
    防止中文乱码

    git config --global core.whitespace cr-at-eol
    git diff的时候忽略换行符的差异, ^M的消除

    git config --global -l 显示所有全局所有git配置

    git config --glabal -e 修改全局配置文件

    git clone
    如果是 `git` 协议需要 ssh密钥
    如果是 `https` 协议不需要密钥,但需要每次输入用户名和密码

##  快捷键

    git init  
    初始化未git仓库

    git add .
    添加所有未添加的文件到暂存区

    git commit --am
    将暂存区文件提交到仓库

    git push orgin master
    把本地当前仓库推送到项目源的主分支 `master`

    git push orgin gh-pages
    把本地当前仓库推送到项目源的分支 `gh-pages`

    git push -f orgin master
    强制推送 (常用来远程仓库回退)

    多用git fetch
	下载到本地后可与本地文件进行比较
    git fetch origin master
    git log -p master..origin/master
    git merge origin/master
	或者
	git fetch origin master:tmp
    git diff tmp
    git merge tmp

    git remote add Org1 git@XXX.git

    git pull Org1 master
    将主项目的地址gitXXX.git@添加远程源Org1
    从Org1远程源拉回代码

    git stash
    将本地修改存储起来

## 分支

    git branch dev
    创建分支dev

    git checkout dev
    切换到dev

    git checkout -b <name>
    创建+切换分支

    git branch
    查看当前分支

    git branch -a
    查看所有分支

    git branch -d <name>
    删除分支

    git merge <name>
    合并某分支到当前分支

## 其他

    git log  后面可以加参数
        --shortstat：只显示--stat中最后的行数添加修改删除统计
        --relative-date：使用较短的相对时间显示

    gls = git log --stat -N (简要显示文件增改行数统计)
    git log -p -N   展开显示每次提交的内容差异，-N 代表最近 N 次
    git log -p filename  显示filename 的提交差异
    git log --name --stat   显示新增、修改和删除的文件清单
    git log --pretty=oneline  显示单行
    git blame filename
    是查看目前的每一行是哪个提交最后改动的

    git rm filename ---  git commit -m 'something'(删除后提交)
    git rm 将工作区和仓库的文件都删除
    git mv

    git show = git show HEAD 查看最近一次提交的更改
    git show tag    查看标签的更改

    gco = git checkcout --filename (用暂存区里的版本替换工作区的版本)

    git checkout -- filename (很常用,本地用来复原的)
    命令中的“--”很重要，没有“--”，就变成了“创建一个新分支”的命令

    git checkout .
    会取消所有本地的修改 (慎用)

    grh = git reset HEAD filename 把暂存区的修改撤销掉，跟HEAD版本里的相同
    git reset --hard HEAD~1     返回到最近的第二次提交

    HEAD 当前版本
    HEAD^ 上一个版本
    HEAD^^ 上上个版本
    HEAD~100 上100个版本

    git reset --hard fd3123    本地仓库跳到`fd3123`提交
    git reflog (查看命令历史，以便回到未来的版本) 开头的id

    同步submodule
    git submodule update --recursive

## 解决冲突

    1. git add
    2. git commit -m 'msg' (可以commit两次,然后一并push)
    3. git pull
    4. git status
    5. 修改有冲突的代码
    6. git add
    7. git commit -m "修改冲突"
    8. git push
