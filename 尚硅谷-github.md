# 创建github项目的步骤

## 初始化文件夹

在一个文件夹内，执行以下命令

```
git init 
```

就可以在文件夹中生成一个隐藏的文件夹，名为.git。说明该文件夹已经是被github管理了。

## 提交文件到git库中的操作

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

## 查看文件提交记录

 操作之后，可以用以下命令查看文件提交记录

```
git log --pretty=oneline 文件名
```

或者用以下命令以简易信息的模式查看。

```
git  log 文件名
```



## 回退到历史版本

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

 

## 删除文件

添加进库之前，用`rm –f 文件名`删除

添加进库之后，用`rm 文件名`删除，并且要用commit提交。

 

## 几种回退的情况

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

git checkout –b test 123