# Git 学习文档

## 1、初始化仓库

1. 创建git仓库

   ```bash
   git init
   ```

   将当前目录创建为git仓库（该目录既可以是空文件夹，也可以是有内容的文件夹），后续该文件夹中的文档文件就由git进行版本控制。

   创建仓库时git会自动添加.git隐藏文件。

   git只能管理文档文件（`TXT`文件、网页、代码等）的内容变化，不能识别媒体文件的内容变化（图片、视频、音频等）。

2. 添加暂存区

   ```bash
   git add readme.txt
   ```

   将`readme.txt`文件添加到到暂存区。

   git add命令成功时不会有提示消息（==Unix的哲学是“没有消息就是做好的消息”，说明添加成功==）。

3. 提交修改

   ```bash
   git commit -m "提交注释"
   ```

   将暂存区的所有文件提交到当前分支，并添加注释。


## 2、查看更改

1. 查看修改文件

   ```bash
   git status
   ```

   查看git仓库中修改后未提交的文件。

2. 查看文件更改内容

   ```bash
   git diff readme.txt
   ```

   如果`readme.txt`被修改，则显示更改内容。

   否则显示`nothing to commit, working tree clean`。

## 3、提交更改

1. 提交修改后的文件

   ```bash
   // 添加暂存区
   git add <fileName>
   // 提交所有暂存到分支
   git commit -m "提交注释"
   ```

   第一步git add， 第二步git commit， git commit可以一次commit多条add。

   `git commit`没有携带`-m "注释信息"`的话会进入`Please enter the commit message for your changes. `页面，进入页面后按`i`或者`insert `在首行输入提交注释，然后按`esc`推出编辑模式，最后在末尾行输入`:wq`退出编辑页面并commit。

## 4、版本回退

1. 查看当前`HEAD`指针指向的版本及历史版本（从当前版本开始往前找，并不会往后找）

   ```bash
   git log
   
   // 格式优化
   git log --pretty=oneline
   ```

2. 版本穿梭，将当前文件回恢复到指定版本

   ```bash
   // 版本号不必写全，前几位即可（四位及以上，太少不能自动补全），git会自动寻找
   git reset --hard <版本号>
   
   git reset --hard HEAD^
   ```

   HEAD表示当前文件最新版本，HEAD^表示上一个版本，HEAD^^表示上上个版本，以此类推。HEAD^100表示前100个版本。

3. 查看历史命令记录

   由于`git log`只能从当前`head`指针指向的版本开始查看历史版本，所以当`head`指针未指向最新版本时，`git log`并不能查看更新的版本，所以如果记不住更新版本的版本号就回不去了。此时使用`git reflog`命令查看历史命令记录：

   ```bash
   git reflog
   ```

## 5、流程图

![Git流程图](image\Git流程图.svg)