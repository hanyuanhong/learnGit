# Git 命令

## 1、git init

```bash
git init
```

将当前目录创建为git仓库（该目录既可以是空文件夹，也可以是有内容的文件夹），后续该文件夹中的文档文件就由git进行版本控制。

创建仓库时git会自动添加.git隐藏文件。

git只能管理文档文件（`TXT`文件、网页、代码等）的内容变化，不能识别媒体文件的内容变化（图片、视频、音频等）。

## 2、git add

将修改内容添加到暂存区

```bash
git add <fileName>
```

## 3、git commit

将暂存区的修改内容提交到分支

```bash
git commit -m "提交注释"
```

## 4、git status

查看状态

```bash
git status
```

## 4、git diff

查看文件修改内容

```bash
// 比较文件与当前版本的差异
git diff <fileName>

// 比较文件与最新版本的差异
git diff HEAD -- <fileName>
```

## 5、git status 与 git diff的区别

- git status

  显示工作空间修改、修改后未添加暂存区、暂存区未提交。

- git diff

  显示具体文件修改内容。

## 6、git log

查看历史版本，从当前版本开始往前找，并不会往后找。

```bash
git log

// 格式优化
git log --pretty=oneline
```

## 7、git reset

1. 将文件恢复到指定版本

   ```bash
   // 版本号不必写全，前几位即可（四位及以上，太少不能自动补全），git会自动寻找
   git reset --hard <版本号>
   
   // HEAD表示当前文件最新版本，HEAD^表示上一个版本，HEAD^^表示上上个版本，以此类推。HEAD^100表示前100个版本。
   git reset --hard HEAD^
   ```

2. 清除已提交的暂存

   ```bash
   git reset HEAD <fileName>
   ```

## 8、git reflog

查看历史命令

```bash
git reflog
```

由于`git log`只能从当前`head`指针指向的版本开始查看历史版本，所以当`head`指针未指向最新版本时，`git log`并不能查看更新的版本，所以如果记不住更新版本的版本号就回不去了。此时使用`git reflog`命令查看历史命令记录：

## 9、git checkout

本质：==用版本库的版本替换工作区的版本==。

撤销修改

- 文件修改后未提交暂存区：撤销到修改之前
- 文件提交到暂存区之后又进行了修改：撤销到提交暂存区之后的状态

```bash
git checkout -- <fileName>
```

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。

## 10、已提交暂存的文件撤销到修改之前

```bash
// 第一步
git reset HEAD <fileName>

// 第二步
git checkout -- <fileName>
```

## 11、git rm

删除本地工作区文件，并添加暂存区。

等同于：手动删除文件 + `git add`。

```bash
git rm <fileName>
```

## 12、本地文件误删以后怎么恢复

```bash
// 用版本库的版本替换工作区的版本
git checkout -- <fileName>
```

## 13、git remote

```bash
// 查看远程库信息
git remote -v

// 本地仓库关联远程库
git remote add origin git@server-name:path/repo-name.git

// 删除关联远程库
git remote rm <远程库名>
```

## 14、git push

本地仓库修改提交到远程库

```bash
git push <关联远程库名> <分支名>
```





# Git流程图

![Git流程图](C:\Users\hanchen\Desktop\git\assets\Git流程图-16798381129781.svg)