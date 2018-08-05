Git is a version control system.
Git is free software.

/**
* git command set
*/

git init ///初始化git库,在项目文件根目录执行

git add xxx ///将文件提交到本地仓库,xxx代表文件

git status xxx ///查看修改的文件,是否有修改或者新增的文件需要提交仓库,是否有文件可以提交新的版本, xxx文件名称,代表查看指定文件,不带xxx则查看项目所有文件状态

git diff xxx ///查看文件文件的修改情况, - 为旧版本内容, + 为修改/新增后的内容, xxx文件名称,代表查看指定文件,不带xxx则查看项目所有文件修改

git commit -m "xxx" ///提交新的版本,双引号里面是对提交版本的说明

git log ///查看提交的历史记录

    参数:
    --pretty=oneline //只显示提交版本号
    参数:
    --graph ///查看分支的合并情况

git reset --hard HEAD~xxx /// xxx代表回溯几个版本,回到指定项目提交版本,注意在指定版本后面的创建的文件与修改的文件都会删除

    简写:
    git reset --hard HEAD^ //代表恢复到上个版本,在HEAD后面 ^ 代表一个版本,例如 ^^ 代表第二个版本,以此类推

    使用版本号:
    git reset --hard xxx //这里的xxx代表版本的哈希值,使用哈希值指定版本,注意这里哈希值只需要版本的前几位数,具体几位数可自行判断,只要唯一即可

git reset HEAD xxx ///xxx代表文件名称,命令将添加在暂存区的文件返回到工作区,就是将add的内容删除

git reflog ///当返回到之前的版本,之后提交的代码将被删除掉,如果过段时间想找回被删除的代码就可以使用 git reflog 找到提交过的版本哈希值,在使用 git reset --hard xxx即可以找回代码

git branch ///查看当前所有分支

    参数:
    xxx //创建一个分支
    例如:
    git branch xxx

    参数:
    -d xxx //删除一个分支
    例如:
    git branch -d xxx

    参数:
    -D xxx //使用-d参数删除分支,前提是必须将分支合并,如果在没有合并的情况下-d是无法删除的,这时可以使用-D参数强制删除
    例如:
    git branch -d xxx

    参数:
    --set-upstream-to xxx origin/xxx //本地分支与远程分支没有链接关系时,使用此参数设置链接
    例如:
    git branch --set-upstream-to test origin/test

git checkout -- xxx ///xxx代表文件名,命令将修改的内容全部撤销,如果有提交使用add命令提交暂存则回到最后暂存时状态否则回到最后提交的版本

git checkout 分支名称 ///切换到指定的分支,切换回master时,子分支提交的文件将暂时不存在版本,需将分支合并

git checkout -b xxx ///xxx代表分支名称,上面两个命令的简写,即创建一个分支,并切换到创建的分支下

git checkout -b xxx origin/xxx ///在本地创建分支并与远程分支同步,xxx可以是同一个命名,也可以不一样

git merge xxx ///xxx代表分支名称,在返回主master分支时需要将子分支提交的文件合并到master,这是一种快速合并,单纯的将master指向xxx

    说明:
    当主分支与其他分支产生冲突时,那么将无法进行合并,需要将冲突解决

git merge --no-ff -m "xxx" ??? ///这是一种合并并提交新的版本信息,xxx代表版本说明,???代表分支名称

git remote add origin xxx ///xxx代表远程仓库地址,命令添加一个远程仓库,这里的仓库是属于自己的仓库

git remote ///查看远程仓库名称

    参数:
    -v 查看库的详细信息,是否有push权限

git push -u origin xxx ///将xxx分支上传到远程仓库中,-u 代表将本地的xxx上传到远程仓库中,并且与远程仓库中的xxx合并

git pull ///从远程仓库同步信息

git rebase ///将远程历史分支文件状态合并到master中,使 git log --graph 分支情况变成一条直线,看上去美观

git clone xxx ///xxx代表远程项目地址,需要在Github上复制开源项目时,一般使用这个命令比较多,支持https协议和基于ssh的git协议

git stash ///保存当前分支的工作,应用场景应该是在需要切换到其他分支工作时,而当前工作并未全部完成,促使你无法提交新的版本,即需要保存当前的工作状态

git stash list ///查看当前所有保存的工作

git stash apply ///恢复工作,但并不删除保存的状态,存储过多次的状态,可以指定恢复的状态

    指定版本:
    git stash apply stash@{???} //???代表版本号一般是0-N的Integer类型

git stash drop ///删除保存的工作状态

git stash pop ///恢复工作状态并删除保存的工作状态

git tag xxx///xxx标签名称

git tag ///查看全部标签

git tag -d xxx///xxx标签名称,命令删除指定名称的tag

git tag xxx ??? ///xxx标签名称,???版本哈希值,命令给指定的版本设置一个tag

git tag -a xxx -m "sss" ??? ///xxx代表tag名称,sss代表tag说明,???代表版本哈希值

git show xxx ///xxx代表tag名称,方法查看版本信息

git push origin xxx ///xxx代表tag名称,将指定标签推送到远程库

git push origin --tags ///将全部标签推送到远程库

git push origin :refs/tags/xxx ///删除远程仓库的标签,xxx代表标签名称

git config ///查看git配置

    参数:
    --list //查看项目配置

    参数:
    --global //查看全局配置