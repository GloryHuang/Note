###Git

####Git安装

 * Window安装
 
   * http://git-scm.com/download/win下载Git客户端软件，和普通软件安装方式一样。
   

 * Linux安装
 
  * CentOS发行版：sudo yum install git

  * Ubuntu发行版：sudo apt-get install git

* Mac安装

  * 打开Terminal直接输入git命令，会自动提示，按提示引导安装即可。
  
####Git工作原理

 * Git管理我们文件的3种状态，分别是已提交（committed）、已修改（modified）和已暂存（staged），由此引入 Git 项目的三个工作区域的概念：Git 仓库、工作目录以及暂存区域。
 
 * Git仓库
 
   * Git仓库目录是Git用来保存项目的元数据和对象数据库的地方。 这是Git 中最重要的部分，从其它计算机克隆仓库时，拷贝的就是这里的数据。
   
   
 * 工作目录
   
   * 工作目录是对项目的某个版本独立提取出来的内容。这些从Git仓库的压缩数据库中提取出来的文件，放在磁盘上供你使用或修改。
   
   
 * 暂存区域
 
   * 暂存区域是一个文件，保存了下次将提交的文件列表信息，一般在Git仓库目录中。有时候也被称作“索引”（Index），不过一般说法还是叫暂存区域。
   
![](/assets/local4.png)

###基本的Git工作流程如下：

* 在工作目录中修改文件。
* 暂存文件，将文件的快照放入暂存区域。
* 提交文件，找到暂存区域的文件，将快照永久性存储到Git仓库目录。


####Git本地仓库
 
 * Git本地仓库指的是开发者开发设备中的仓库。
 
###Git基础 

 * 命令行方式：任意目录（建议开发根目录）右键 > Git Bash Here
 
 
####1.配置用户

 * 配置用户的意义在于记录开发者信息,以便在版本控制记录开发者的操作行为,如lion于2017-08-24解决了一个bug。
 
* git config --global user.name "自已的名字"
* git config --global user.email "自已的邮箱地址"
* --global 配置当前用户所有仓库
* --system 配置当前计算机上所有用户的所有仓库

* 注：配置用户只需要执行1次，可以重复使用。

####2.初始化仓库

 * 如果想要利用git进行版本控制，需要将现有项目初始化为一个仓库，或者将一个已有的使用git进行版本控制的仓库克隆到本地。
 
#####如果是一个新项目 

 * **git init**
  
  ![](/assets/git1.png)
  
  ** git init**只是创建了一个名为.git的隐藏目录，这个目录就是存储我们历史版本的仓库，ls -al 可以查看
   
   ![](/assets/git2.png)
   
#####假如公司已有项目用了Git，那我们就利用克隆

 * **git clone 仓库地址**
 
  ![](/assets/git3.png)
  
 * 执行完这个命令，会在当前目录下生成一个Monment目录（默认和仓库名称相同），这个便是已有一个使用Git管理的项目。
 
  ![](/assets/git4.png)
  
####3.查看文件状态

 * 初始化仓库后便可以进行开发了，进入到刚刚创建好并初始为仓库的目录，添加我们开发需要的文件。
通过**git status**可以检测当前仓库文件的状态

  ![](/assets/git5.png)
  
  * 注：**git会忽略空的目录**
  
####4.添加文件到暂存区

 * 假设经过一段时间的开发后，需要把已开发的部分存起来，使用git add添加到暂存区。
 
  * **git add 文件名/ 文件路径 “*”或-A代表所有**
  ![](/assets/git6.png)
 
 * 放到暂存区的文件被标记成了**绿色**，等待提交。
 
   * 注：颜色是工具给添加的，目的是增加可读性并不是git统一的。
   
####5.撤销更改 

 * 继续我们的开发、再次**git status**可以再次查看仓库状态
 
  ![](/assets/git7.png)

 * 又经过一段时间后发现新开发的部分有Bug，想要回到之前状态，可以使用**git checkout 文件名**。
 
  ![](/assets/git8.png)
  
   * 注：从暂存区还原原到工作区
   
####6.提交文件

 * 经过一个相对较长阶段开发或者一个功能开发完成了，就可以提交到本地仓库了，永久保存了。
 
  * **git commit -m '备注信息'**
  
    ![](/assets/git9.png)
   
   * 将暂存区被标记成绿色的文件，**全部提交到本地仓库存储**。
   
   * 这时git status查看状态(没有什么可提交的，变的很干净。)
   
    ![](/assets/git10.png)
   
####7.查看提交历史   

 * 反反复复开发了很多的功能了，通过git log查看一下提交的历史。
 
   ![](/assets/git11.png)
   
   commit 81b1e4fc2ae178caedf4575596377a80a6f1e73f
   代表一次提交的唯一ID，一般称为SHA值
  * 注：按键盘q键退出。

####8.再次检测仓库文件状态

 * 隔了好些天后，继续开发

   * git status 查看状态
  
   * 又提示有修改，等待重新添加到暂存区。
   
     ![](/assets/git12.png)
    

####9.重新添加暂存区然后提交

   ![](/assets/git13.png)
   
   
####10.再次查看历史

 * git log 可查到所有提交历史
 
  * 这时可以查看到更多提交历史。
  
   ![](/assets/git15.png)
  
####11.恢复上一次提交的状态
 
  * 通过SHA值可以回到之前某一次的提交（时光倒流）
  
  * **git reset --hard c888a614e072e2这样便回到了支付功能的状态**
  * **git log再次查看发现最后一次提交成了支付功能了**

 ![](/assets/git16.png)
 
 
###仓库示意图

 ![](/assets/gitres.png)
 
 
###Git分支

 * 在我们的现实开发中，需求往往是五花八门的，同时开发个需求的情况十分常见，比如当你正在专注开发一个功能时，突然有一个紧急的BUG需要你来修复，这个时候我们当然是希望在能够保存当前任务进度，再去修改这个BUG，等这个BUG修复完成后再继续我们的任务。如何实现呢？
 
  *  **通过Git创建分支来解决实际开发中类似的问题**。
  
  
 * 在Git的使用过程中一次提交称为历史记录（版本），并且会生成一个唯一的字符串，如下图
 
  ![](/assets/git17.png)
  
  * 这个串可以代表某一个历史版本（**实际使用只取前面几位就可以**），
  
  
 * 所有的提交（commit）实际上都是在分支（branch）的基础上进行的。
 
  ![](/assets/git18.png)
  
 * 当我们在初始化仓库的时候（实际上是产生第1次提交时），Git会默认帮我们创建了一个master的分支，并且有指针（HEAD）指到了末端。
 
 * 指针（HEAD）用来标明当前处于哪个分支的哪个版本，如上图指的处于master分支的最后1个版本。


###创建自已的分支

####1.创建分支
  
   * **git branch hotfix**
  
    * 新的分支会在当前分支原有历史版本的结点上进行创建，我称其为子分支如下图
    
     ![](/assets/git19.png)


    * 新建的子分支会继承父分支的所有提交历史。
    
    
####2.切换分支

 * **git checkout hotfix**
 
  ![](/assets/git20.png)
  
   * 我们发现HEAD现在又指向了hotfix的末端
   
####4.再次提交操作 

 * 修改bug后，提交
 
   ![](/assets/git21.png)
   
   * 这次的提交历史版本就会记录在hotfix这个分支上了，并且HEAD伴随hotfix在移动。
   
####5.当我们再次切回到master时

  ![](/assets/git22.png)
  
  * 当我们切换回master后，HEAD指向了master分支的末端，并且我们观察发现我们的文件内容还是原来的“模样”。
  
####6.继续之前的开发

  ![](/assets/git23.png)
  
  
  * 总结: 
  
   * 当我们git checkout branchname时，HEAD会自动指向对应分支的末端，工作目录中的源码也会随之发生改变。
    
   * 这个时候我们就在hotfix这个分支上修复了这个BUG，而我们原来在master分支上的操作并未受到影响
   
####7.合并（融合）分支

   ![](/assets/git24.png)
 
   * 这时master会有两个父结点了，master便包含了hotfix里的修复了
   
####8.删除分支
  
   * **git branch -d hotfix**
   
   * 这时用来修复BUG创建的hotfix分支已经没有用处了，我们可以将它删除。
   
   ![](/assets/git25.png)
   
   
###Git远程（共享）仓库

  * 借助一个远程仓库，可以共享代码、历史版本等数据.
  
####创建共享仓库

  * Git要求共享仓库是一个以**.git**结尾的目录。
  
   * mkdir repo.git 创建以.git结尾目录
   * cd repo.git 进入这个目录
   * git init --bare 初始化一个共享仓库，也叫裸仓库 **注意选项--bare**
   
    ![](/assets/git45.png)

  * 这时这个仓库是一个空的仓库，并且不允在这个仓库中进行任何修改。
  
####向共享仓库共享（同步）内容
  
  * 将自已开发的项目同步到这个目录中，其它开发者就可以共享你开发的项目了。
  
   * 进入到yike目录
   
   * git push ../repo.git master  (这样便把yike中的项目同步进了repo.git中)
   
     ![](/assets/git26.png)
     
####从共享仓库里取出内容

 * 新创建一个目录（模拟另一个开发者）
 
 * git clone ./repo.git demo  (通过repo.git共享仓库，我们轻松得到了一个yike的副本)
 
  ![](/assets/git27.png)
  
####通过demo仓库向repo.git共享内容

  * 进入到demo里，我们做一些修改

   * cd demo

   * git push ../repo.git master
 
   ![](/assets/git28.png)
   
   
####在360仓库从repo.git获取共享的内容

 * cd yike
 
 * git pull ../repo.git master
 
  ![](/assets/git30.png)


###命令汇总

 * git config配置本地仓库
   * 常用git config --global user.name、git config --global user.email
 * git config --list查看配置详情
 * git init 初始一个仓库，添加--bare可以初始化一个共享（裸）仓库
 * git status 可以查看当前仓库的状态
 * git add“文件” 将工作区中的文件添加到暂存区中，其中file可是一个单独的文件，也可以是一个目录、“*”、-A
 * git commit -m '备注信息' 将暂存区的文件，提交到本地仓库
 * git log 可以查看本地仓库的提交历史
 * git branch查看分支
 * git branch“分支名称” 创建一个新的分支
 * git checkout“分支名称” 切换分支
 * git checkout -b deeveloper 他健并切到developer分支
 * git merge“分支名称” 合并分支
 * git branch -d “分支名称” 删除分支
 * git clone “仓库地址”获取已有仓库的副本
 * git push origin “本地分支名称:远程分支名称”将本地分支推送至远程仓库，
 * git push origin hotfix（通常的写法）相当于
 * git push origin hotfix:hotfix
 * git push origin hotfix:newfeature

 * 本地仓库分支名称和远程仓库分支名称一样的情况下可以简写成一个，即git push “仓库地址” “分支名称”，如果远程仓库没有对应分支，将会自动创建

 * git remote add “主机名称” “远程仓库地址”添加远程主机，即给远程主机起个别名，方便使用
 * git remote 可以查看已添加的远程主机
 * git remote show “主机名称”可以查看远程主机的信息


###Git高级

 * gitignore忽略文件
 
  * 在项目根目录下创建一个.gitignore文件，可以将不希望提交的罗列在这个文件里，如项目的配置文件、node_modules等
  
  * https://github.com/github/gitignore


 * 比较差异
  
  * 当内容被修改，我们无法确定修改哪些内容时，可以通过git diff来进行差异比较。

  * git difftool 比较的是工作区和暂存的差异
  * git difftool “SHA”比较与特定提交的差异
  * git difftool “SHA”“SHA”比较某两次提交的差异
  * git difftool 分支名称 比较与某个分支的差异
  
  
 * 回滚（撤销）操作
  
  * HEAD 默认指向当前分支的“末端”，即最后的一次提交，但是我们通过git reset 可以改变HEAD的指向。
  
    ![](/assets/s.png)

 * git reset
   * --hard 工作区会变、历史(HEAD)会变， 暂存区也变
   * --soft 只会变历史(HEAD)
   * --mixed（默认是这个选项）历史(HEAD)会变、暂存区也变，工作区不变

* git checkout

 * git checkout SHA -- "某个文件"，代表只是从SHA这个版中取出特定的文件，和git reset 是有区别的，reset 重写了历史，checkout 则没有。


 * 更新仓库
 
  * 在项目开发过程中，经常性的会遇到远程（共享）仓库和本地仓库不一致，我们可以通过git fetch 命令来更新本地仓库，使本地仓库和远程（共享）仓库保持一致。
  
  
 * git fetch  “远程主机”
   
   * git fetch “远程主机” “分支名称”

          
 * 利用git fetch 获取的更新会保存在本地仓库中，但是并没有体现到我们的工作目录中，需要我们再次利用git merge来将对应的分支合并（融合）到特定分支。如下
 
   * git pull origin 某个分支， 上操作相当于下面两步
   * git fetch 
   * git merge origin/某个分支
   
   
 * 查看远程主机上总共有多少个分支
 
   * git branch -a 便可以查看所有(本地+远程仓库)分支了
   
    ![](/assets/git32.png)

* 删除远程分支git push origin --delete 分支名称
* 删除远程分支git push origin :分支名称
