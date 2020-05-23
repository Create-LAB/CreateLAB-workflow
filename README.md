# CreateLAB-workflow
关于CreateLAB的工作流程以及代码规范

# Git使用规范
## 一、分支管理策略
### 主分支 master
1.分支说明：master分支是提供给用户使用的正式版本，也就是完成品。

2.注意事项：首先每个项目代码库只有一个主分支。主分支的代码是当前稳定的最新版本。master的管理与合并仅由一人完成，只给一个人权限，这样方便管理代码。

### 开发分支 develop
1.分支说明：用于日常开发的分支

2.分支命名规则：dev_v1.0，其中v代表开发版本

3.注意事项：Develop分支是当前在开发中的最新版本代码，并且创建辅助分支要基于Develop分支。

### 辅助分支 feature or bug
1.分支说明：辅助分支是用来添加新功能和解决bug的分支。项目需要增加的新功能需求和bug需求会在issue中提出，之后需要新建辅助分支来解决。

2.命名规则：issue#编号_简要标题

3.注意事项：辅助分支是基于develop分支建立的。在开发的过程中要经常与主干保持同步，若出现冲突要在本地进行解决。最终合并到develop分支后，需要自行删除辅助分支。

## 二、git workflow工作流图
![](https://github.com/Create-LAB/CreateLAB-workflow/blob/master/git%20criterion/375020183.jpg) 
## 三、issue建立规范
1.所有的任务均需要在github上建立issue，每个issue需要assign给相应的人去处理。
2.在projects中可以对所有issue进行排期，这样可以很好的跟踪每个issue的完成情况。
![](https://github.com/Create-LAB/CreateLAB-workflow/blob/master/git%20criterion/cut1.jpg) 
3.issue的颗粒度尽量小，而且需要有明确的范围以及完成标准。
## 四、项目的命名规范
1.项目的功能比较单一，那么只需要以功能来对仓库进行命名，首字母要大写。

2.项目的功能模块比较多的情况，需要使用 “产品_模块”来对仓库进行命名，或者想一个概括性的名字。

## 五、常用命令介绍
1.新建分支

创建分支 git checkout 命令是切换分支，加上参数 -b 表示如果分支不存在，就创建，且立即切换到新创建的分支

git checkout -b myfeature

2.分支开发

添加工作区改变的文件到暂存区，尽量git add file1 file2, 不提倡 git add *

git add *

查看当前工作区的状态

git status

把暂存区的内容放入版本库，加入verbose参数会对变化进行比较并显示

git commit --verbose

3.与主干同步

git fetch origin

4.推送代码到远端

git push -u origin myfeature
