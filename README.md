### 一、Git与常用的版本控制工具CVS,SVN等不同，它采用了分布式版本库的方式，不必服务器端软件支持。
***
### 二、GIT不仅仅是个版本控制系统，它也是个内容管理系统(CMS),工作管理系统等。
*Git 与 SVN 区别点：*  
1. GIT是分布式的，SVN不是：这是GIT和其它非分布式的版本控制系统，最核心的区别。  
2. GIT把内容按元数据方式存储，而SVN是按文件：所有的资源控制系统都是把文件的元信息隐藏在一个类似.svn,.cvs等的文件夹里。  
3. GIT分支和SVN的分支不同：分支在SVN中一点不特别，就是版本库中的另外的一个目录。  
4. GIT没有一个全局的版本号，而SVN有：目前为止这是跟SVN相比GIT缺少的最大的一个特征。  
5. GIT的内容完整性要优于SVN：GIT的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。  

#### 集中式和分布式的区别  
**集中式(svn,cvs) －－ 集中式版本控制系统**，版本库是集中存放在中央服务器的，而干活的时候，用的都是自己的电脑，所以要先从中央服务器取得最新的版本，然后开始干活，干完活了，再把自己的活推送给中央服务器。中央服务器就好比是一个图书馆，你要改一本书，必须先从图书馆借出来，然后回到家自己改，改完了，再放回图书馆。集中式版本控制系统最大的毛病就是必须联网才能工作，如果在局域网内还好，带宽够大，速度够快，可如果在互联网上，遇到网速慢的话，可能提交一个10M的文件就需要5分钟，这还不得把人给憋死啊。  
**分布式** －－ 分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库。这样，工作的时候，就不需要联网了，因为版本库就在自己的电脑上。既然每个人电脑上都有一个完整的版本库，那多个人如何协作呢？比方说你在自己电脑上改了文件A，你的同事也在他的电脑上改了文件A，这时，你们俩之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。分布式版本控制系统通常也有一台充当“中央服务器”的电脑，但这个服务器的作用仅仅是用来方便“交换”大家的修改，没有它大家也一样干活，只是交换修改不方便而已。和集中式版本控制系统相比，分布式版本控制系统的安全性要高很多，因为每个人电脑里都有完整的版本库，某一个人的电脑坏掉了不要紧，随便从其他人那里复制一个就可以了。而集中式版本控制系统的中央服务器要是出了问题，所有人都没法干活了。      
***
### 三、git工作流程:  
* 克隆 Git 资源作为工作目录。  
* 在克隆的资源上添加或修改文件。
* 如果其他人修改了，你可以更新资源。
* 在提交前查看修改。
* 提交修改。
* 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。  
***
### 四、工作区、暂存区和版本库
+ 工作区：就是你在电脑里能看到的目录。
+ 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
+ 暂存区：Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。
***
### 五、创建仓库和常用git命令
git init：初始化一个git仓库，Git的很多命令都需要在Git的仓库中运行。可以使用一个已经存在的目录作为Git仓库。在执行命令完成后，Git仓库会生成一个.git目录，该目录包含了资源的所有元数据，其他的项目目录保持不变（Git只在仓库的根目录生成.git目录）。  
git init newrepo：初始化后，会在newrepo目录下会出现一个名为.git的目录，所有Git需要的数据和资源都存放在这个目录中。
如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：  
`git add *.c        //将以.c结尾的文件提交到仓库`  
`git add README     //将README文件提交到仓库`  
`git commit -m '初始化项目版本'`
`git clone <repo> <directory>    //将远程Git仓库克隆到指定的目录`   
`repo:Git仓库`  
`directory:本地目录`  
**默认情况下，Git 会按照你提供的 URL 所指示的项目的名称创建你的本地项目目录，通常就是该 URL 最后一个 / 之后的项目名称。如果你想要一个不一样的名字，你可以在该命令后加上你想要的名称。**  
`mkdir html                  //可以创建一个html的文件夹`  
`git init                //通过git init命令把这个目录变成Git可以管理的仓库。`  
`git pull               //将远程库上面的内容拉到本地库`  
`git add .           //将当前文件夹所有文件添加到缓存`  
`git commit -m "初始化项目版本"         //将缓存区内容添加到仓库中`  
`git push            //将本地库的内容推送到远程仓库`

***
### 六、配置用户名和邮箱地址(git是分布式的，所以每个机器都必须自报家门)  
`$ git config --global user.name "name"`  
`$ git config --global user.email "test@hhh.com"`  
`--global表示这台机器上所有Git仓库都会使用这个配置,当然也可以对某个仓库指定不同的用户名和Email地址`

***
### 七、git reset --hard HEAD^ 可以回退到上一版本，`git checkout -- <file>`撤销修改  
`git log --pretty=oneline       //可以查看历史纪录的版本号`  
`git reset --hard commit_id(十六进制的版本号)       //可以指定会到某一版本`  
Git的版本回退速度非常快，因为Git在内部有个指向当前版本的HEAD指针  
Git提供了一个命令git reflog用来记录你的每一次命令  
`git checkout -- <file>`可以丢弃工作区的修改，手动把文件恢复到上一个版本的状态。  
`git checkout -- readme.txt`意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：这里有两种情况：  
1. 一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态;
2. 一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。  
**Tip: git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令，我们在后面的分支管理中会再次遇到git checkout命令。**

***
### 删除文件：  
命令git rm用于从版本库中删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，git checkout -- file能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容。 git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。 

***
### 远程仓库  
1. 第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：ssh-keygen -t rsa -C "youremail@example.com";邮箱换成自己的邮箱。如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。  
2. 第2步：登陆GitHub，打开“Account settings”，“SSH and GPG Keys”页面：然后，点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容  
为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。  
当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。github上面的东西是公开看得到的，要想别人看不到，自己搭一个git服务器，公司内部开发必备。  
#### 添加远程库  
- 先有本地库，后有远程库的时候，如何关联远程库  
    - 在本地仓库运行命令`git remote add origin git@github.com:williamChann/learngit.git`可将本地库与github上面的远程仓库相关联。添加后，远程库的名字就是`origin`，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。  
    - 把本地库的所有内容推送到远程库上:`git push -u origin master`。由于远程库是空的，第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。  
    - 此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；  

---
#### 假设我们从零开发，那么最好的方式是先创建远程库，然后，从远程库克隆｀git clone git地址｀  
### 分支管理  
#### 创建和合并分支  
1. 创建`dev`分支，然后切换到`dev`分支: `git checkout -b dev`(git checkout命令加上-b参数表示创建并切换 = `git branch dev` `git checkout dev`);
2. 用`git branch`命令查看当前分支:当前分支前面会标一个`*`号
3. 可以在`dev`分支上面做修改提交，但是切回到`master`分支的时候，修改的内容会不见的，因为刚才的提交是在`dev`分支上，`master`的提交点没有变，这时候就可以合并两个分支了。
**总结**
- 查看分支:`git branch`
- 创建分支:`git branch <name>`
- 切换分支:`git checkout <name>`
- 创建和切换分支:`git checkout -b <name>`
- 合并某分支到当前分支:`git merge <name>`
- 删除分支:`git branch -d <name>`

#### 解决冲突
当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
`git log --graph`和`git log --graph --pretty=oneline --abbrev-commit`都可以查看分支的合并情况

#### 分支管理策略
- 首先，`master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
- 平时干活都在`dev`分支上，也就是说，`dev`分支是不稳定的，到某个时候，比如1.0版本发布时，再把`dev`分支合并到`master`上，在`master`分支发布1.0版本；
- 团队开发时每个人都在`dev`分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。  
而合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并。例如`git merge --no-ff -m "merge with no-ff" dev`，因为本次合并要创建一个新的commit，所以加上`-m`参数，把描述写进去。而fast forward合并就看不出来曾经做过合并。
	
#### Bug分支
- 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
- 当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场。
- 还有一种恢复方法是是用`git stash apply`恢复，但是恢复后，stash内容并不删除，需要用`git stash drop`来删除；
- [参考BUG分支](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)

#### Feature分支
- 在实际的开发中，每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。
- 如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除。

#### 多人协作
**推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：**
-  `master`分支是主分支，因此要时刻与远程同步；
- `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

