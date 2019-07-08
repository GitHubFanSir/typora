# 创建github项目的步骤

### 初始化文件夹

在一个文件夹内，执行以下命令

```
git init 
```

就可以在文件夹中生成一个隐藏的文件夹，名为.git。说明该文件夹已经是被github管理了。

### 提交文件到git库中的操作

新建一个文件，此时文件还只是在一个普通的文件夹中，并没有被github管理，此时可以用以下命令把该文件纳入github的管理系统（添加到暂存区）。

```
git add 文件名
```

管理之后，才可以进行提交的操作。只有提交之后，才代表该文件被纳入github的本地库中了。提交的命令是

```
git  commit  –m “注释内容” 文件名
```

在每一步的操作后，都可以使用以下命令查看此时github库的状态，颜色都会不一样

```
git  status
```



每次都会出现以下警告

> warning: LF will be replaced by CRLF

可以用以下命令进行屏蔽。

```
git config --global core.autocrlf false
```

 

# 版本穿梭

 

先把已存在本地库中的文件进行修改，连续修改几次。修改之后都进行add和commit操作

### 查看文件提交记录

 操作之后，可以用以下命令查看文件提交记录

```
git log --pretty=oneline 文件名
```

或者用以下命令以简易信息的模式查看。

```
git  log 文件名
```



### 回退到历史版本

 回退到上一次提交

```
git reset --hard HEAD^  
```

回退n次操作

```
git reset --hard HEAD~n  
```

 版本穿越

执行以下命令查看历史记录的版本号

```
 git  reflog  文件名
```

执行以下命令穿梭到对应的版本

```
  git  reset  --hard  7位版本号
```

6.还原文件

git  checkout -- 文件名  

 

### 删除文件

添加进库之前，用`rm –f 文件名`删除

添加进库之后，用`rm 文件名`删除，并且要用commit提交。

 

### 几种回退的情况

1变更，没有add，没有commit

```
git checkout --文件名
```

2变更，有add，没有commit，执行以下命令把暂存区的修改撤销掉(*unstage*),重新放回工作区

```
git reset HEAD 文件名
```

3变更，有add，有commit

```
git reset --hard HEAD^
```

 

# git的三个区

- 工作区(Working Directory):  就是你电脑本地硬盘目录
- 本地库(Repository):  工作区有个隐藏目录.git，它就是Git的本地版本库
- 暂存区(stage):  一般存放在"git目录"下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。

![clip_image001](尚硅谷-github.assets/clip_image001.jpg)



# 分支

如下图，系统上线了，但是产品经理又提了新的需求，评估一下工期要两个月，但是同时系统正在上线运行，时不时还要修改bug，如何管理几个版本？

![1562590786940](尚硅谷-github.assets/1562590786940.png)

### 创建分支

```
git  branch  <分支名>

git branch –v  查看分支
```



### 切换分支

```
git checkout  <分支名>

一步完成： git checkout  –b  <分支名>
```



### 合并分支

```
先切换到主干   git  checkout  master

git  merge  <分支名>
```



### 删除分支

```
先切换到主干   git  checkout  master

git  branch -D  <分支名>
```

 

# 冲突

冲突一般指同一个文件同一位置的代码，在两种版本合并时版本管理软件无法判断到底应该保留哪个版本，因此会提示该文件发生冲突，需要程序员来手工判断解决冲突。



### 合并时冲突

程序合并时发生冲突系统会提示CONFLICT关键字，命令行后缀会进入MERGING状态，表示此时是解决冲突的状态。

![1562591011452](尚硅谷-github.assets/1562591011452.png)

![1562591287275](尚硅谷-github.assets/1562591287275.png)

### 解决冲突

通过git diff 可以找到发生冲突的文件及冲突的内容。

![1562591916040](尚硅谷-github.assets/1562591916040.png)

然后修改冲突文件的内容，再次`git add <file>` 和`git commit` 提交后，后缀MERGING消失，说明冲突解决完成。

![1562591940059](尚硅谷-github.assets/1562591940059.png)

# Git 常用命令小总结

   mkdir：         		                          XX (创建一个空目录 XX指目录名)
   pwd：          		                           显示当前目录的路径。
   git init         		                            把当前的目录变成可以管理的git仓库，生成隐藏.git文件。
   touch           	                               xx文件或者新建文件
   git add XX      	                            把xx文件添加到暂存区去。
   git commit –m “XX”                  	提交文件 –m 后面的是注释。
   git status        	                           查看仓库状态
   git diff  XX      	                            查看XX文件修改了那些内容
   git log          		                           查看历史记录
   git reset  --hard HEAD^	           版本回退
   cat XX         		                            查看XX文件内容
   git reflog       	                             版本穿梭，查看历史记录的版本号id
   git checkout -- XX  	                   把XX文件在工作区的修改全部撤销。
   git rm XX          	                          删除XX文件
   git remote add origin https://github.com/zzyybs/testgit 	 关联一个远程库
   git push –u(第一次要用-u 以后不需要) origin master 		     把当前master分支推送到远程库
   git clone https://github.com/arjrzhouyang/testgit  		       从远程库中克隆
   git checkout –b dev  				                                                    创建dev分支 并切换到dev分支上
   git branch  			                      查看当前所有的分支
   git checkout master 		          切换回master分支
   git merge dev    		                  在当前的分支上合并dev分支
   git branch –d dev 	               	删除dev分支
   git branch name                 		创建分支
   git remote                       			查看远程库的信息
   git remote –v 	                     	查看远程库的详细信息
   git push origin master      		Git会把master分支推送到远程库对应的远程分支上 



# Github简介与实操

### 是什么

​	GitHub是一个Git项目托管网站,主要提供基于Git的版本托管服务

![1562592412398](尚硅谷-github.assets/1562592412398.png)

创建SSH Key：

```
ssh-keygen -t rsa -C   你自己用户邮箱
```

成功的话会在~/下生成.ssh文件夹

![1562592539966](尚硅谷-github.assets/1562592539966.png)

生成之后，把id-rsa.pub文件里的内容复制，粘贴到GitHub设置中的SSH and GPG keys中即可。然后运行以下命令测试是否可以连通

```
ssh -T git@github.com
```

连通之后，在github上新建一个仓库，建成之后会有如图片所示的提示

![1562601469751](尚硅谷-github.assets/1562601469751.png)

按照提示，在本地仓库中打开bash，输入给出的两行代码，就可以和GitHub进行关联了。

```
git remote add  <远端代号>   <远端地址> 
```

<远端代号>  是指远程链接的代号，一般直接用origin作代号，也可以自定义。

<远端地址>   默认远程链接的url



把本地库的内容推送到远程git push命令，实际上是把当前分支master推送到远程

```
git push -u origin master
```

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。



不过有一点不舒服的就是，每次push都需要输入账户名和密码。此时可以用以下方式操作，就可以避免了。

在 “C:\用户\自己的账号” 的目录下新建名字为_netrc的文件并编辑该文件写如下内容：

> machine github.com
> login 你自己github登陆用户名
> password 你的密码

<div style="color:#00F">我字体是蓝色</div>





