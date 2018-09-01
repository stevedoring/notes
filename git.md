- [Git的安装](#git%E7%9A%84%E5%AE%89%E8%A3%85)
- [创建版本库](#%E5%88%9B%E5%BB%BA%E7%89%88%E6%9C%AC%E5%BA%93)
- [添加与提交](#%E6%B7%BB%E5%8A%A0%E4%B8%8E%E6%8F%90%E4%BA%A4)
- [查看工作区状态](#%E6%9F%A5%E7%9C%8B%E5%B7%A5%E4%BD%9C%E5%8C%BA%E7%8A%B6%E6%80%81)
- [版本回退](#%E7%89%88%E6%9C%AC%E5%9B%9E%E9%80%80)
- [撤销修改](#%E6%92%A4%E9%94%80%E4%BF%AE%E6%94%B9)
- [删除及恢复](#%E5%88%A0%E9%99%A4%E5%8F%8A%E6%81%A2%E5%A4%8D)
- [远程仓库](#%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93)
- [分支管理](#%E5%88%86%E6%94%AF%E7%AE%A1%E7%90%86)
- [标签管理](#%E6%A0%87%E7%AD%BE%E7%AE%A1%E7%90%86)
--- 
## Git的安装
- 直接安装`sudo apt install git`
- 源码安装：
    - 使用`wget`下载源码
    - `./config`
    - `make`
    - `make install`
- 安装后配置
```
git config --global user.name "name"
git config --global user.email "emain@example.com"
```
> `global`参数是全局参数，表示该台电脑上所有的版本库都使用该配置。
---
## 创建版本库
- 选择一个位置，创建一个目录。
- 在该目录下，使用`git init`来将当前目录创建成版本库。
---
## 添加与提交
- 使用`git add <file>`将文件添加到暂存区，可一次添加多个文件，可以多次使用。
- 使用`git commit -m <note>`将暂存区的文件提交到版本库，`-m <note>`是输入本次提交的说明，这样就可以从提交记录中明确每次的修改点。
---
## 查看工作区状态
- 使用`git status`可以查看当前工作区状态。
- 使用`git diff <file>`可以对比查看修改内容。
- 使用`git diff HEAD --<file>`可以查看当前版本内容和版本库里的差异。
---
## 版本回退
- `git log`可以查看当前提交历史记录。
- `git -reset --hard HEAD^`删除当前记录后回退到上一版本。
- `git -reset --hard commit_id`回退到commit_id版本，该版本之后的记录会被删除。
- `git -revert HEAD^`新建一个commit，内容是上次提交之前的内容。
- `git reflog`查看命令历史记录。
---
## 撤销修改
- `git checkout --<file>`可以丢弃当前工作区的修改
    - 当file修改后还没添加到暂存区，使用`git checkout`后，会回到和版本库里相同的状态。
    - 当file修改后添加到了暂存区，而后又做了修改，此时使用`git checkout`后，会回到添加到暂存区时的状态。
---
## 删除及恢复
- 删除有两种操作：
    - 在本地删除后，使用`git commit`确认删除。
    - 使用`git rm <file>`删除文件，再使用`git commit`来从版本库确认删除。
- 在删除后，如果发现误删，可以使用`git checkout --<file>`来从版本库恢复文件。
---
## 远程仓库
- 本地建立的仓库推送到远程仓库：
    1. 关联远程仓库：`git remote add origin git@github.com:name/rsp.git`
    2. 推送到远程仓库：`git push -u origin master`
    > github里远程仓库默认名为origin。   
    > `git push`命令，实际上是把当前分支master推送到远程。  
    > 由于远程库是空的，我们第一次推送master分支时，加上了`-u`参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
    - 随后只要本地做了修改，只需要通过`git push origin master`推送到远程库。 
- 从远程库克隆到本地仓库。使用`git clone git@github.com:name/rsp.git`即可。
---
## 分支管理

---
## 标签管理
