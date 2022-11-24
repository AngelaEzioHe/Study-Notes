# Git用法（基础）

## 使用之前

- ``git config  - -global user.name "提交人"``
- ``git config  - -global user.email "邮箱地址"``

## 提交步骤

1. ``git init`` 初始化git仓库
2. ``git status`` 查看文件状态
3. ``git add 文件名`` 提交文件到暂存区
4. ``git commit -m 提交信息`` 向仓库中提交代码
5. ``git log`` 查看提交记录

## 撤销指令

``git rm  - -cached 文件名`` 将文件从git的暂存区中移除

``git checkout 文件名`` 将不正确修改的文件返回成暂存区中的文件。（即用原本的文件覆盖新的、未托管的文件）

``git reset  - -hard 文件ID`` 将git仓库中指定的更新记录恢复出来，并且**覆盖**暂存区和工作目录（电脑上的文件夹）；即只保留ID对应的文件，其余的删除掉。

