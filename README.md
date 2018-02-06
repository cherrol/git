#Git 常用操作和指令   

##配置git    

```git config --global user.name 'Your Name'  //  配置名字```   
```git config --global user.email 'example@example.com'  //  配置邮箱```   

---
##创建版本库   

```mkdir xxx       //  新建文件/文件夹```   
```cd xxx       //  进入xxx文件夹下边```   
```pwd     //  显示当前项目路径```   
```git init    //  把当前目录变为Git版本管理仓库```   
```git add readme.md       //  把readme.md放到暂存区```   
```git commit -m 'add readme.md'   //  把暂存区的文件提交到仓库```   
第一次修改 -> git add -> 第二次修改 -> git add -> git commit   

---   

##仓库状态管理      

```git status  //  查看当前仓库状态```   
```git diff readme.md  //  查看readme.md修改的内容```   
要随时掌握工作区的状态，使用git status命令。   
如果git status告诉你有文件被修改过，用git diff可以查看修改内容。   
    
```git log     //  查看历史记录```   
```git log --pretty=oneline    //查看历史记录简要信息   输出：commitID+提交的注释```   
```git reset --hard HEAD~1(HEAD^)      //回退到上N个版本~1(HEAD^),~2(HEAD^^)数字代表返回到上几个版本```   
```git reset --hard 3628164    //3628164是版本号，指定版本号可以回退到指定版本```   
```git reflog      //记录下来的每一次版本更换命令```   
```cat readme.md   //查看readme.md内容```   
```git diff HEAD -- readme.md      //查看readme.md本地文件和仓库的区别```   
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。   
穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。   
要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。   

```git checkout --file     //丢弃工作区域的修改```   
```git reset HEAD file     //取消保存到暂存区的修改```   
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。   
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到     了场景1，第二步按场景1操作。   
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。   

```rm demo/add.txt      //删除add.txt```   
```git rm demo/add.txt      //删除仓库里的add.txt```   
```git commit -m 'remove add.txt'   //提交删除```   

```git remote add origin  https://github.com/TriteLove/learngit.git     //第一次关联本地仓库和服务器仓库```   
```git push -u origin master        //第一次提交仓库代码```   
```git push origin master       //提交本地仓库代码```
 
 ---
 
##远程仓库    

要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git   
关联后，使用命令git push -u origin master第一次推送master分支的所有内容   
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改   
