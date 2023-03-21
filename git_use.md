# git使用教程
## git简介
git是分布式的 SVN集中式的

区别在于集中式的版本控制系统每次在写代码时都需要从服务器中拉取一份下来，并且如果服务器丢失了，那么所有的就都丢失了，你本机客户端仅保存当前的版本信息，换句话说，集中式就是把代码放在一个服务器上集中管理，你的所有回滚等操作都需要服务器的支持。

分布式的区别在于，每个人的电脑都是服务器，当你从主仓库拉取一份代码下来后，你的电脑就是服务器，无需担心主仓库被删或者找不到的情况，你可以自由在本地回滚，提交，当你想把自己的代码提交到主仓库时，只需要合并推送到主仓库就可以了，同时你可以把自己的代码新建一份仓库分享给其它人。

像集中式它们都有一个主版本号，所有的版本迭代都以这个版本号为主，而分布式因为每个客户端都是服务器，git没有固定的版本号，但是有一个由哈希算法算出的id，用来回滚用的，同时也有一个master仓库，这个仓库是一切分支仓库的主仓库，我们可以推送提交到master并合并到主仓库上，主仓库的版本号会迭代一次，我们客户端上的git版本号无论迭代多少次，都跟master无关，只有合并时，master才会迭代一次。

![图片](https://pic1.zhimg.com/80/v2-cd9ae639fa7ba273ffc3753037629ee0_720w.webp)

## git相关命令

初始化git，有两种方式：
``` git
# 方式一:本地生成一个git
git init
# 方式二:从远端克隆一个仓库
git clone https://gitee.com/xxxxxx/xx.git
```
基本配置
```
# 配置用户名
git config --global user.name "name"
# 配置邮箱
git config --global user.email "name@mail.com"
```
删除远程仓库
```
git remote rm origin
```
添加远程仓库
```
git remote add origin https://gitee.com/xxxxxx/xx.git
```
推送至远程仓库

将已修改文件添加至暂存区
```
git add dir/filename # 添加指定文件
git add . # 添加所有已修改文件
```
将暂存区的改动提交到本地的版本库，使用git commit命令我们就会在本地版本库生成一个40位的哈希值，用于版本回退
```
git commit -m "message" 
# message就是本次提交的简要说明
```
本地上传，注意在推送前需要先从远程拉取
```
git push -u origin master # master可以更换为其他分支
```
从远程仓库拉取
更新本地：
```
git pull origin master # master可以更换为其他分支
```

查看状态
```
git status
git diff git_use.md
```

查看历史修改
```
git log
```
现在，我们要把当前版本append GPL回退到上一个版本add distributed，就可以使用git reset命令：
```
$ git reset --hard HEAD
HEAD is now at e475afc add distributed
```


