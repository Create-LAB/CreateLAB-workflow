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

# python 代码规范

## 为什么要规范代码？

1. 增加易读性，容易维护，能够提高效率
2. 好的代码规范能够体现一个程序员的专业性

## python命名规范

1.类的命名方法
大驼峰命名：类名中的所有单词的首字母都要大写，并且不使用特殊字符、下划线和数字。

~~~python
class LinearClassify(object): ✔️
class Linear_Classify(object): ❌
class linearclassify(object): ❌
~~~

2.函数命名
函数的命名要全小写，多单词时要用下划线连接

~~~python
def linear_classify(): ✔️
def __linear_classify(): ✔️ #内建函数
def Linear_classify(): ❌ 
def linearclassify(): ❌
~~~

3.常量命名
全部大写字母，可加下划线和数字

~~~python
MAX_SIZE=100
~~~

## python注释

复杂的逻辑要写注释，这样方便阅读与维护
单行注释： 如果注释独占一行，那么#顶头，空一格之后再写注释; 如果是行尾注释，那么先空两格写#，之后再空一格写注释的内容

~~~python
# 代码注释
def linear_classify():  # 代码注释
~~~

## docstrings

在python中，比较推崇在代码中写文档，代码即文档，比较方便，容易维护，直观，一致。通过编写docstrings能够非常方便的编写api文档。尽量为每个主要的函数方法编写docstrings。

推荐使用numpy格式的docstrings，可以在pycharm里设置docstrings的格式。

~~~python
def detect(
        cfg,
        data_cfg,
        weights,
        images='data/samples',  # input folder
        output='output',  # output folder
        fourcc='mp4v',
        img_size=416,
        conf_thres=0.5,
        nms_thres=0.5,
        save_txt=False,
        save_images=True,
        webcam=True
):
    """
    Loading the trained model to detect whether a individual is wearing a mask.
    If not,a voice alert will be given.
    Parameters
    ----------
    cfg: str
        The path of the model cfg.
    data_cfg: str
        The path of the data cfg.
        eg. data/mask.data
    weights: str
        The path of the weights file.
    images: str,'data/samples'
        The path of the images for detect.
    output: str
        If you want to save the detected result, you should set it.
    fourcc: str
        Four character code,use in cv2.VideoWriter_fourcc
    img_size: int
        The size of the image loaded.
    conf_thres: int
    nms_thres: int
    save_txt: bool
        If ypu want to write bounding boxes and labels of detections into txt.
    save_images: bool
        If you want to save image.
    webcam: bool
        If you want to open the camera.
    """
~~~

##  python代码的排版

对于python代码的排版问题，只要使用autopep8就能够自动的排版，写完代码之后使用该工具对代码进行排版的规范化。

~~~
pip install autopep8
~~~
假如有个代码demo.py

~~~
autopep8 --in-place --aggressive --aggressive demo.py
~~~

可以在pycharm里设置autopep8
