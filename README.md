# 或许是介绍Android Studio使用Git最详细的文章 666
**欢迎访问我的[个人博客网站](http://www.wensibo.top)**
## 前言
**本文较长，图片很多很多，流量党慎入**
使用Git已经有一段时间了，但是之前都是使用`Git Bash`，在Android Studio上使用Git一开始不是很习惯，就像用惯了SVN来使用Git一样，琢磨了一段时间的Android Studio，也看了我觉得为数不多但是很有质量的介绍AS的书籍 `《Android Studio实战 快速、高效地构建Android应用》`，强烈安利大家哦！所以就写了这篇文章跟大家一起学习如何在Android Studio高效地使用Git。另外如果大家想要拿来学习的话可以直接fork[我的项目](https://github.com/Wensibob/MyGit) 。
另外一点需要说明的就是本文中大量使用Android Studio的快捷键，如果你不熟悉，可以看看我的[另外一篇文章](http://www.wensibo.top/2017/03/09/Android%20Studio%E5%BF%AB%E6%8D%B7%E9%94%AE%E6%80%BB%E7%BB%93/) 。

## 安装Git
我使用的是Windows，所以我这里只能介绍Windows下安装Git的过程了。
点[这里](https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fgit)选择符合你的版本，直接安装就行了。
安装完成之后，在开始菜单中找到`Git-->Git Bash`，如果出现类似下面的对话框的话就证明安装成功了。
![Git界面](/screenshots/1.PNG)
安装成功之后，需要配置一下你的信息，直接在上面的命令行中输入以下命令：
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
>**注意：
1.将上方的`Your Name`换成你自己的名字，随意起都行。
2.将上方的`email@example.com`换成你自己的邮箱。
3.讲一下`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。**

## Android Studio配置Git
使用快捷键`Ctrl+Alt+S`打开Settings，接着点击`Version Control --> Git `在`Path To Git Executable`上输入Git的存放位置，如下图：
![Git Path](/screenshots/2.PNG)
之后点击旁边的Test按钮，如果出现如下的成功提示，说明Git配置成功。

![Git Success](/screenshots/3.PNG)

接着按照下图配置你的Github账号密码，输入完成之后点击Test按钮，如果账号密码都正确的话就会提示成功，那么就可以继续往下走了：
![Github Account](/screenshots/4.PNG)

## 创建本地仓库
不管你是刚刚新建的项目，亦或是已经写好的项目，进行的操作都是一样的。
这里我以新建一个名为[MyGit](https://github.com/Wensibob/MyGit)的项目为例子，如果你想练习，也可以到[这里](https://github.com/Wensibob/MyGit)fork一下。
对于一个已经新建好的项目，找到菜单栏上的VCS，按照下图进行操作：

![创建本地仓库](/screenshots/5.PNG)

选择项目的根目录为git初始化的目录：

![初始化目录](/screenshots/6.PNG)

初始化之后你会发现原本文件的文件名都是**白色**的，现在变成了**棕色**，这表示文件已经被git跟踪了，但是并没有添加到仓库中：

![棕色目录](/screenshots/7.PNG)

## 忽略文件
我们知道，在git初始化一个仓库的时候会自动生成一个.gitignore文件，这个文件用来忽略那些不用加入到仓库的文件，在我们这个工程中总共生成了两个.gitignore文件，分别是在项目根目录下，以及在app文件夹下。我们可以对这些文件进行编辑，表示我们需要忽略哪些文件，但是一般情况下，我们选择默认就好，除非你有需要就进行适当的修改：

![.gitignore](/screenshots/8.PNG)

## 添加文件
添加文件就如git命令中的`git add`，在Android Studio中add的方式有四种，但是都是大同小异，让我来一一举例：

**1.选中项目的根目录，右键选中Git，再选中Add，如下图：**

![第一种add方式](/screenshots/9.PNG)

**2.选中项目根目录，点击菜单栏中的VCS菜单，选中Git-->Add，如下图：**

![第二种add方式](/screenshots/10.PNG)

**3.使用快捷键`Alt+9`，或者点击屏幕下方的Version Control工具按钮**

打开版本控制的窗口，可以看到应该是如下图的样子，该窗口有两个下拉栏，一个是Default，用来记录已经添加的文件，另一个是Unversioned files，用来记录已经被跟踪但是未添加的文件。

![Version Control](/screenshots/11.PNG)

右键Unversioned files，选中Git-->Add，如下图：

![第三种add方式](/screenshots/12.PNG)

**4.使用快捷键`Ctrl+Alt+A`**


add之后文件名变成了**绿色**，这是代表已经添加进仓库为文件，接下来就可以commit文件了，使用快捷键`Ctrl+K`或者选中工程根目录右键`Git-->Commit Directory`可以调出commit窗口，如下所示，在其中选择你想要提交的文件，填写提交的信息，在Author文本框中可以填写提交此次提交的操作者名字，如果不填写的话，就会默认是之前配置Github账号的用户名。可以看到，提交之后文件名重新变回了熟悉的**白色**。

![首次提交](/screenshots/13.PNG)

提交成功之后，你可以使用快捷键`Alt+9`，或者点击屏幕下方的Version Control工具按钮，切换到Log菜单查看Log日志，如下图所示：

![首次提交Log日志](/screenshots/17.PNG)

## 如何clone项目
使用Git clone项目到本地中是很简单的，在Android Studio中也是如此，首先找到你喜欢的项目，fork到你自己的仓库之后，点击Clone or Download按钮，复制地址，如下图所示：

![github 复制地址](/screenshots/14.PNG)

接下来回到Android Studio，按照下图的操作可以打开clone的对话框，在地址栏中粘贴刚才复制的地址，点击Test按钮，测试是否可以通过，如果成功，那么久可以点击Clone导入项目了。

![clone项目](/screenshots/15.PNG)

![Clone Test](/screenshots/16.PNG)

_____________________________________________________________________________

>** 回到我们最开始讲的[MyGit项目](https://github.com/Wensibob/MyGit)，首先我们需要模仿一下在日常开发中使用Git的情形，例如我们经常会在分支上进行工作，所以熟练地掌握分支工作的流程以及技巧是十分重要的，接下来我会使用具体的例子跟大家一起了解如何在Android Studio上使用分支进行开发。
以下举得例子将会围绕Git的一种工作模式，即：`Git Flow`，如果你对此不是很了解，那么推荐你[阮一峰老师的文章](http://www.ruanyifeng.com/blog/2015/12/git-workflow.html) 。**

_____________________________________________________________________________

## Git flow
Git flow是广泛采用的一种工作流程

![Git_flow工作流程图](/screenshots/git-workflow.png)

他的主要特点有两个：

**1.首先，项目存在两个长期分支**

>* 主分支master
* 开发分支dev


前者用于存放对外发布的版本，任何时候在这个分支拿到的，都是稳定的分布版；后者用于日常开发，存放最新的开发版。

**2.其次，项目存在三种短期分支**

>* 功能分支（feature branch）
* 补丁分支（hotfix branch）
* 预发分支（release branch）


## 新增功能1——显示Hello World
正如我们在介绍Git flow介绍的，master分支只是用于产品的发布，在平时的开发中是不会使用它的，而只会使用dev分支，但是如果我们有了新的功能，一般是会在dev分支中在创建一条该功能的分支，所以我们应该这样做。
### 创建dev、feature-1分支，并且我们需要转到feature-1分支上
在Android Studio中，我们可以很方便的管理分支，在主界面的右下角，点击Git可以出现当前的分支，默认为master，我们选中`New Branch`，如下图所示：

![add_branch_feature-1 ](/screenshots/19.PNG)

在弹出的对话框中我们输入`feature-1`，点击OK，这样我们不仅新建了feature-1分支，并且正处于该分支中，接下来按照同样的方法创建dev分支，如果不出意外的话，我们现在应该是处于dev分支上，但是因为我们现在要开发功能1，所以必须转换到`feature-1`分支上，按照下图的操作，我们能够回到feature-1分支上。

![come back to feature-1](/screenshots/20.PNG)

接下来打开Log，我们应该能够看到如下的情景：

![log for add two branches](/screenshots/21.PNG)

可以看到我们现在有三个分支：master、dev、feature-1，但是AS提示我们应该有四条分支，其实HEAD就是当前活跃分支的游标。形象的记忆就是：你现在在哪儿，HEAD 就指向哪儿，所以 Git 才知道你在那儿！不过 HEAD 并非只能指向分支的最顶端，实际上它可以指向任何一个节点，它就是 Git 内部用来追踪当前位置的标记。我们可以使用下面的图来演示当前分支的情况：

![branch_picture_1](/screenshots/branch_picture_1.png)

### 完成功能1
```java
/**
     * feature-1
     * display HelloWorld
     * @param view
     */
    public void feature1(View view) {
        if (btn_feature_1.getText().toString().equals("功能1")) {
            btn_feature_1.setText(R.string.feature_1_dis);
        } else {
            btn_feature_1.setText(R.string.feature_1);
        }
    }
```
好了，功能1编写完成，那么就提交吧！老方法：Ctrl+K进行提交，按照下图填写提交信息，每一次的提交信息最好能够详细并且格式规范，这样以后再查看Log的时候就会比较方便。

![add feature-1 on feature-1](/screenshots/22.PNG)

点击Commit按钮提交完毕之后，可以看到现在的log图变成了下图：

![log after add feature-1](/screenshots/23.PNG)

我们可以打开Log图的右侧，他列出了目前正在被Git跟踪的所有文件，我们选中MainActivity.java，点击上边的第二个按钮`Show Diff(显示差异)`：

![show diff](/screenshots/24.PNG)

在弹出的界面中可以显示该文件的当前版本和master分支中的该文件的差异，我们可以使用`Esc`快捷键退出该界面，如下图所示：

![diff1 on MainActivity.java](/screenshots/25.PNG)

### 将feature-1分支合并到dev分支上
如下图所示，选中dev分支并选择checkout：

![chose dev](/screenshots/26.PNG)

你会发现现在代码回到了最开始的状态，现在选中feature-1分支并选中merge，准备将feature-1分支合并到dev分支上：

![merge feature-1 to dev](/screenshots/27.PNG)

再来重新看一下Log图，他长下面这样，可以看到现在feature-1分支已经与dev分支合并，并且现在他们是处于同一状态的：

![log after merge to dev](/screenshots/28.PNG)

最后的最后，我们需要删除已经完成任务的feature-1分支，以免分支过多管理混乱。

![delete branch feature-1](/screenshots/29.PNG)

## 新增功能2——显示Hello Android
同样的道理，我们可以按照如下的步骤这样做：

**1.迁出dev分支，并且新建分支`feature-2`之后迁出`feature-2`分支，具体的步骤我就不再演示了，跟上面的是一样的。**

**2.开始撸代码。**
```java
 /**
     * feature-2
     * display HelloAndroid
     * @param view
     */
    public void feature2(View view) {
        if (btn_feature_2.getText().toString().equals("功能2")) {
            btn_feature_2.setText(R.string.feature_2_dis);
        } else {
            btn_feature_2.setText(R.string.feature_2);
        }
    }
```
**3.使用快捷键Ctrl+K提交feature-2的修改，并填写提交信息。**

![add feature-2 on branch feature-2](/screenshots/30.PNG)

**4.切换回dev分支并且合并feature-2分支之后删除feature-2分支。**

如果不出错的话，你的Log应该是下面这样的：

![log after delete feature-2](/screenshots/31.PNG)

## 在dev分支上增加功能3——Hello Java
同样的道理，这里我就不再一一演示，如果按照上面的步骤做的话，最后的Log应该是这样的：

![log after add feature-3 on dev](/screenshots/32.PNG)

## 重点来了，老板说了，新开发的功能3不喜欢，需要删除了功能3，咋办呢？
这里就需要讲到Git的回退了，在Android Studio中提供了两种回退的方式：Git revert以及Git reset。
### Git revert
Git revert可以将版本回退到上一步，但是会新增一个提交，他的流程就像下面这幅图一样：

![git_revert_picture_2](/screenshots/git_revert_picture_2.png)

**1.首先打开Log，找到功能3的提交，右键选择复制哈希码(Copy Revision Number)，如下图所示：**

![Copy Revision Number](/screenshots/34.PNG)

**2.打开Android Studio的终端Terminal，他就在Version Control的旁边，之后输入以下命令按回车键：**
```
git revert 9c834d8c66598fb132a0cc8e4c1f8c341d058f3e
```
>那一段很复杂的数字字母就是我们刚才复制的哈希码

如下图所示：

![git revert on terminal](/screenshots/35.PNG)

**3.之后终端会列出此次提交的具体信息，如果确认要回退，请输入`:q`保存此次操作并且退出会话
现在你可以看到，他确实增加了一次提交，并且回到了上一版的内容，Log应该是这样的：**

![log after revert](/screenshots/36.PNG)

### Git reset
相比之下，Git reset就要干脆的多，与Git revert的功能一样，它也可以将代码恢复到上一个版本，但是不会新增一次提交，他的流程如下：

![git_reset_picture_3](/screenshots/git_reset_picture_3.png)

因为我们需要删除功能3，并且让Log看起来并没有revert的这一次提交，所以我们应该在dev分支上后退两步，确实是这样的对吧！

**1.点击菜单栏上的`VCS-->Git-->Reset HEAD`，打开对话框，在To Commit文本框中输入`HEAD~2`，就像下图这样：**

![reset HEAD](/screenshots/37.PNG)

![reset HEAD~2](/screenshots/38.PNG)

**2.点击Reset按钮之后，你可以发现Log变了，变回原来那个熟悉的画面了：**

![log after reset](/screenshots/31.PNG)

## master分支上被修改了 
突然你发现你的同事在master分支上提交了两次，分别是增加了功能1和功能4，但是其中的功能1很显然`HelloWorld`被写成了`WorldHello`，例如这样的：
```java
 /**
     * feature-1
     * display WorldHello
     * @param view
     */
    public void feature1(View view) {
        btn_feature_1.setText(R.string.feature_1_dis);
    }

    /**
     * feature-4
     * display Hello
     * @param view
     */
    public void feature4(View view) {
        btn_feature_4.setText(R.string.feature_4_dis);
    }
```
提交更改，之后Log应该是这样的：

![log after add feature-1&4 on master](/screenshots/40.PNG)

我们依旧用演示图表示当前分支的发展情况：

![branch_picture_4](/screenshots/branch_picture_4.png)

## Rebase
老板说了，master分支只要功能4不需要功能1，而dev分支上的功能1、2全部都要合并到master分支上。那么这个时候我们就可以使用rebase了。
git rebase用于把一个分支的修改合并到当前分支。现在我们切换到master分支，将dev上的做修改加入到master中，所以我们选择rebase，在Android Studio中提供了功能十分强大的rebase。

**1.点击菜单栏上的VCS-->Git-->Rebase，如下图所示：**

![git rebase](/screenshots/41.PNG)

**2.在弹出的对话框中，我们在Onto的下拉栏中选中dev分支，表示我们需要将master分支rebase到该分支下。**

![git rebase branch](/screenshots/42.PNG)

**3.点击`Rebase`之后，你会发现Android Studio弹出对话框，显示master分支的两次提交，需要我们做出选择，如下图所示：**

![git start rebasing](/screenshots/43.PNG)

**4.因为我们不需要master分支上的功能1但是需要功能4，所以在功能1的提交上我们选择skip(跳过这个提交)，在提交4上选择pick(挑选此次这个提交)，点击 `Start Rebasing`，我们可以看到又有对话框弹出，此次是让我们对每个文件进行挑选，如下图所示：**

![rebase conflict](/screenshots/44.PNG)

**5.对于每一个文件，你可以选择接受你的那一部分，或者接受另一只分支上的内容，又或者你可以点击Merge对文件进行筛选。我们点击`Merge`按钮，可以看到有三个文件呈现在屏幕上。其中中间的文件是最后的结果，左边的为当前分支master分支，右边的为dev分支，你还可以发现在修改过的每一行中都存在一个`X >>`符号，点击`X`表示不需要这一行的修改，点击`>>`表示接受这一行的修改，我们甚至还可以像在编辑器中那样复制、粘贴、编辑内容，我们最终作出的选择如下图所示，之后可以点击Apply进行保存，如果你不想保存，那就点击Abort终止此次修改：**

![conflict between files](/screenshots/45.PNG)

**6.对于剩下的两个文件也做相同的处理，之后我们可以看到master分支已经有了dev分支的功能1和功能2和自身的功能4，并且去掉了自己之前的功能1，可以看一下Log，如下所示：**

![log after rebase](/screenshots/46.PNG)

我们依旧使用演示图来表示最后的分支情况：

![branch_picture_5](/screenshots/branch_picture_5.png)

## 推送到远程仓库
推送很简单，你可以导航到菜单栏`VCS-->Import Into Version Control -->Share Project on Github`，如下图所示：

![push](/screenshots/47.PNG)

在弹出的对话框中填写远程仓库的名称，点击Share：

![share](/screenshots/48.PNG)

之后你就可以在你的[Github](https://github.com/Wensibob/MyGit)上面看到这一次的推送了。

## 本地所做的修改如何同步到远程仓库
现在我需要在工程中加入一些文件，例如说我新建了一个`screenshots`文件夹，并在其中添加了这篇文章需要用到的截图，那么如何将这些文件一起同步到远程仓库呢？其实很简单。

**1.使用快捷键`Alt+9`或者点击工具按钮打开`Version Control`，右键`Unversioned Files`，选择`Git-->Add`，将所有文件加入Git中，如下图：**

![add files](/screenshots/49.PNG)

**2.右键Default，选择Commit所有的文件之后填写提交信息，如下图：**

![commit files](/screenshots/50.PNG)

**3.使用快捷键`Ctrl+Shift+K`或者右键工程根目录，选择push项目，如下图所示：**

![push project](/screenshots/51.PNG)

**4.在弹出的对话框中点击`Push`按钮，就可以将所做的修改同步到远程仓库了，如下图：**

![push!](/screenshots/52.PNG)

**5.对于修改过的文件想要同步到远程仓库，按照同样的步骤就行了，这里不再赘述了。**

## 后记
这篇文章有点长，图也很多，我也写了很久，有的时候思路不清晰也混了(尴尬脸)，所以难免会有错误，还请大家批评指正，大家互相学习，希望你能够学到更多Android Studio的知识。
