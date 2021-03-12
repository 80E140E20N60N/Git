1.2. 为什么要使用版本管理工具
-----------------

在做英雄案例时，要实现五大功能，每一个功能写完以后，为了方便查看都是单独保存成一个文件，通过 vscode 对比两个文件可以看出它们之间的差别，你的文件列表可能就像下面的截图。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/1.png)

但是在真正开发过程中，我们会随时修改很多个文件，那么这些文件修改以后都通过上述方式管理，会给我们带来相当大的工作量，从而容易出错，并且我想要切换回到某一个版本，根本都搞不清楚哪些文件需要切回去。基于此种问题，我们在软件开发过程中，公司都会引入**版本管理工具**来自动帮助我们达成这项工作

1.3. 版本管理工具的分类
--------------

> 版本管理工具分为三大类：
> 
> *   本地版本控制工具，是最早期的版本控制工具，现在已经完全不使用了，典型代表软件：RCS
> *   集中式版本控制工具，如：SVN
> *   分布式版本控制工具，如：Git

### 1.3.1. 本地版本控制工具

> 只能单机运行，不支持多人协作开发，如果版本库数据损坏，所有的历史记录会丢失

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/2.png)

### 1.3.2. 集中式版本控制工具

> 典型软件代表：SVN
> 
> 集中式版本控制工具特点：版本库是集中存放在服务器上的，编程人员在开发的时候要先从中央服务器取得最新的版本，代码编写完成后再把自己的代码推送给服务器保存起来
> 
> 通俗理解：服务器就好比是一个图书馆，你现在要修改一本书，必须先从图书馆借出来，然后回到家自己改，改完后再放回图书馆。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/3.png)

#### 1.3.2.1. 优点

*   支持多人协作开发

#### 1.3.2.2. 缺点

*   必须联网才能工作，如果不联网，用户本地就看不到历史版本，也切换不了版本
*   如果服务器损坏，那么所有的版本数据都会丢失

### 1.3.3. 分布式版本控制工具

> 典型软件代表：Git，现在使用最广泛，最流行
> 
> 分布式版本控制工具特点：所有版本信息在每个使用者电脑上都保留了一份，可以离线在本地提交，只需在连网时提交到相应的服务器或其他用户那里即可，支持多人协作开发。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/4.png)

#### 1.3.3.1. 优点

*   断网后支持离线本地版本提交，联网后再同步到服务器即可
*   每个用户那里保存的都是所有的版本数据，只要有一个用户的设备没有问题就可以恢复所有的数据，
*   支持多人协作开发

#### 1.3.3.2. 缺点

*   由于保存所有版本数据，占用空间较大

1.4. Git 安装和配置
--------------

### 1.4.1. windows 下 git 安装

*   首先，你需要到 git 官网 `https://git-scm.com/download/win` 下载并一路下一步直到安装完毕

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/5.png)

*   随便进入一个文件夹中鼠标右键，在弹出菜单中点击 "Git Bash Here" 打开 git 终端即表示安装成功
    
    ![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/7.png)
    

### 1.4.2. Mac 电脑下 git 安装

> 通过 homebrew 安装 Git，步骤如下

*   启动 Mac 电脑终端，输入如下指令回车
    
    ```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    
    
    ```
    
*   在 Mac 电脑终端输入如下指令安装 git
    
    ```
    brew install git
    
    
    ```
    
*   在 Mac 电脑终端输入 git ，出现如下界面表示成功
    
    ![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/6.png)
    

### 1.4.3. 配置邮箱和名字

如果是第一次使用 git，需要使用`git config`配置提交者信息，因为以后需要多人开发时，可以区分不同的修改者。

```
git config  --global user.name "自己的用户名"
git config  --global user.email "自己的正确的邮箱"

# 查看配置信息
git config --list


```

1.5. git 管理文件基本流程
-----------------

> 任务：在桌面上创建一个名称为 "git 练习" 文件夹，其中使用 zhangsan.txt 文件存储张三的语文，数学成绩数据，语文成绩先出来，数学成绩晚出来 1 天，所以要分两个版本来存储张三的成绩：
> 
> 版本 1：在 zhangsan.txt 中存储张三的语文成绩，分数随便填
> 
> 版本 2：在 zhangsan.txt 中存储张三的数学成绩，分数随便填

任务执行步骤前置准备：

*   在桌面中创建一个名称为 **git 练习**的文件夹
    
*   在 git 练习文件夹中创建一个 **zhangsan.txt** 文件
    
*   以下任务执行步骤均在 **git 练习**这个文件夹中打开 git bash 进行，具体操作为：在 git 练习文件夹中鼠标右键，选择 “git Bash Here” 打开 git 命令窗口，以下命令均在打开的 git 命令窗口中执行
    
    ![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/git.gif)
    

### 1.5.1. git 操作流程演示

> 将 zhangsan.txt 文件添加到 git 仓库操作步骤：

<table><thead><tr><th>任务步骤</th><th>命令</th><th>效果</th></tr></thead><tbody><tr><td>创建版本库（Repository）</td><td>git init</td><td>自动生成了隐藏的 .git 的文件夹，命令只需只需一次<img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/8.png"></td></tr><tr><td>添加语文成绩数据</td><td></td><td>打开 zhangsan.txt，添加语文: 98<img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/9.png"></td></tr><tr><td>让 git 跟踪<br>zhangsan.txt 文件</td><td>git add zhangsan.txt</td><td>通过 git status -s 查看到 zhangsan.txt 文件的状态为 A<img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/12.png"></td></tr><tr><td>将 zhangsan.txt<br>添加到 git 仓库</td><td>git commit -m ‘新增语文成绩'</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/13.png"></td></tr><tr><td>查看提交历史记录</td><td>git log</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/14.png">证明已经成功提交到了 git 仓库</td></tr><tr><td>查看 zhangsan.txt<br>的状态 - 复杂版</td><td>git status</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/10.png"> 上图是刚创建 zhangsan.txt 文件时的复杂状态信息</td></tr><tr><td>查看 zhangsan.txt<br>的状态 - 简单版</td><td>git status -s</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/11.png">上图是刚创建 zhangsan.txt 文件时的简单状态信息</td></tr></tbody></table>

### 1.5.2. 修改 zhangsan.txt git 管理

> 在 zhangsan.txt 中添加数学成绩后，演示 git 管理修改过的文件

<table><thead><tr><th>任务步骤</th><th>命令</th><th>效果</th></tr></thead><tbody><tr><td>添加数学成绩数据</td><td></td><td>打开 zhangsan.txt，添加数学: 90<img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/15.png"></td></tr><tr><td>查看此时 zhangsan.txt 的状态</td><td>git status -s</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/16.png">当文件未被跟踪时，M 为红色</td></tr><tr><td>让 git 跟踪<br>zhangsan.txt 文件</td><td>git add zhangsan.txt</td><td>当文件被跟踪以后，再次执行 git status -s<br>可以查看到 M 变成了绿色<img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/17.png"></td></tr><tr><td>将 zhangsan.txt<br>添加到 git 仓库</td><td>git commit -m ‘新增数学成绩'</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/18.png"></td></tr><tr><td>查看提交历史记录</td><td>git log</td><td><img class="" src="http://157.122.54.189:9092/upload/zybdoc/git/imgs/19.png">证明新增数学成绩的修改数据已经成功添加到了 git 仓库</td></tr></tbody></table>

### 1.5.3. 版本回滚

> 需求：目前 git 版本库中已经有 2 个版本了，第一次是语文成绩的版本，第二次是数学成绩的版本，目前仓库中的版本指向的是数学成绩版本，如果想要回滚到语文成绩的版本，操作如下：

#### 1.5.3.1. 查看 git 版本库中所有版本号

```
在命令窗口中执行： git log


```

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/20.png)

#### 1.5.3.2. 回滚到语文成绩版本

语文成绩版本的版本号为：9f022bf1756310746fd48b52777adcc3c387df0d

在命令窗口执行如下命令即可回滚

```
//语法：git reset --hard 版本号
git reset --hard 9f022bf1756310746fd48b52777adcc3c387df0d


```

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/21.png)

1.6. git 中的三大区域
---------------

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/22.png)

### 1.6.1. 工作区

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/23.png)

### 1.6.2. 暂存区

前面我们把文件往 Git 版本库里添加的时候，是分两步执行的：

用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

### 1.6.3. git 版本库

用`git commit`提交更改，实际上就是把暂存区的所有内容提交到版本库的当前分支，默认是 master 分支

我们通过 git init 创建 Git 版本库时，Git 自动为我们创建了唯一一个`master`分支，所以 git commit`就是往`master 分支上提交更改，将来我们还可以创建新的分支更加方便管理

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/24.png)

1.7. 添加远程仓库
-----------

> 特点：先有本地库，后有远程库

### 1.7.1. 国外远程仓库 - github(网络慢)

前面 git 版本库中的代码如果需要同步给他人一起开发就需要用到远程仓库来进行托管。

目前，全球最大的代码托管仓库是 [www.github.com，国内也有 [码云](https://gitee.com/) 提供代码托管服务，它们俩的使用方式是一样的，只不过 github 是国外的，访问速度会很慢，码云是国内的，访问速度很快。](http://www.github.com，国内也有[码云](https://gitee.com/)提供代码托管服务，它们俩的使用方式是一样的，只不过github是国外的，访问速度会很慢，码云是国内的，访问速度很快。)


#### 1.7.1.2. github 新建空白仓库流程

1、当登录 [www.github.com 以后，按照下图就可以创建一个 git 仓库](http://www.github.xn--com%2Cgit-8t3kfdro97d7fc226is0gdoao62bsywolkx3bhx4b5h6e/) `注意：务必要先登录`

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/25.png)

2、新建 git 仓库成功页面

> 在此页面上有两大块 git 命令提示，根据图片中注释按照实际情况操作即可

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/27.png)

3、向空白仓库初次提交代码

> 进入到 g**it 练习**文件中打开 git 命令窗口输入如下命令将本地代码推送到 github 服务器中

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/githubpush1.gif)

4、后续的提交代码方式

> 上面已经掌握了如何向一个空白仓库提交代码的操作
> 
> 本节主要学习如何向仓库中第二次及其后续的代码提交方式
> 
> 需求：向 zhangsan.txt 文件中增加了数学成绩以后，需要再次提交到 github 仓库中，在 git 窗口操作如下:

1、`git add .` // 最后的点 表示添加工作区中所有新增、修改、删除的文件进入暂存区

2、`git commit -m '新增数学成绩'` // 提交暂存区的所有文件到本地仓库

3、`git push origin` // 将本地仓库版本推送到 github 仓库中

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/githubpush2.gif)

### 1.7.2. 国内远程仓库 - 码云 (网络快)

#### 1.7.2.2. 码云新建空白仓库流程

1、当登录 [www.gitee.com 以后，按照下图就可以创建一个 git 仓库](http://www.gitee.xn--com%2Cgit-8t3kfdro97d7fc226is0gdoao62bsywolkx3bhx4b5h6e/) `注意：务必要先登录`

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/28.png)

2、新建仓库成功页面

> 在此页面上有两大块 git 命令提示，根据图片中注释按照实际情况操作即可

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/29.png)

1.8. 从远程库克隆
-----------

> 特点：先找到远程库，后克隆到本地

当我们在 github 或者码云这些远程仓库中看到别人分享出来的很有用的源码时，通常想拿下来研究一下，这时就需要用到 git 的克隆。

举例：我们在 [www.gitee.com 上看到了 layui 这个前端框架功能很强大，想下载下来研究一下，步骤如下：](http://www.gitee.com上看到了layui这个前端框架功能很强大，想下载下来研究一下，步骤如下：)

1、点击 [https://gitee.com/sentsin/layui](https://gitee.com/sentsin/layui) 进入 layui 仓库

2、点击面板上的`克隆/下载` 后选择 HTTPS，点击`复制`按钮复制 layui 仓库的地址：[https://gitee.com/sentsin/layui.git](https://gitee.com/sentsin/layui.git)

3、在桌面新建一个文件夹名字叫：`layui研究`

4、在`layui研究`文件夹中打开 git 命令窗口执行：git clone [https://gitee.com/sentsin/layui.git](https://gitee.com/sentsin/layui.git)

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/38.png)

**注意：git clone 别人仓库中文件，在本地修改以后是没有权限 git push 的，这是需要 Fork 到自己账号中**

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/40.png)

1.9. Fork 远程仓库代码
----------------

> Fork 的意义：把别人的仓库开一个分支到自己账号中，再克隆自己仓库中的源码后，本地修改源码有权限 git push 到自己的远程仓库

需求：需要把 layui 的源码 Fork 一份到自己账号中

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/39.png)

注意：git clone 自己账号中的代码就有权限 git push 到远程仓库了

1.10. git 相关命令
--------------

### 1.10.1. 初始化仓库

> 我们需要创建一个版本库，需要在该目录执行`git init`命令。
> 
> 我们一般把这种具有版本控制功能的目录称为**工作区**

```
命令： git init


```

执行完毕后，在项目根目录会有一个`.git`文件夹，该文件用来记录版本信息，出现该文件说明已经创建成功。但请注意，因为`.git`文件是一个隐藏文件，资源管理器没法看到。

### 1.10.2. 将文件添加到暂存区

> 命令：git add 文件名 或者 . 或者 *

举例：

```
// 指定一个文件名
git add 文件名1

// 指定多个文件名
git add 文件名1  文件名2

// . 或者 * 代表添加所有文件
git add .
或者
git add *


```

### 1.10.3. 将暂存区的文件提交到仓库

> 命令： git commit -m '描述本次提交文件的作用，方便其他人查看'

举例：

```
git commit -m '描述本次提交文件的作用，方便其他人查看'


```

### 1.10.4. 检查文件状态

> 命令：
> 
> git status 命令可以 打印出文件的详细状态
> 
> git status -s 命令可以打印出文件的简要状态

```
// 打印出文件的详细状态
git status 

// 打印出文件的简要状态
git status -s


```

不同标记代表的含义

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/309.png)

### 1.10.5. 查看历史版本

```
git log


```

> 下图查看到所有仓库的历史版本:

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/31.png)

### 1.10.6. 代码回滚（危险操作 - 慎重）

> 通过`git reset --hard 后面跟版本号` 可以使本地仓库代码回滚到指定版本
> 
> **危险操作 - 慎重**：此操作会把不属于此版本的所有文件和修改的内容全部删除

```
语法：
git reset --hard 版本号 

举例：
git reset --hard 683222716cf61c6e67e46ac33cc4c75db80100a1


```

1.11. 分支管理
----------

git 的分支就像王者荣耀游戏里三条路，每条路的英雄可以自己补兵对线，他们补兵对线获得的经验和金币是互相独立，互不影响的。git 中的分支也具有相同的特性，分支的代码互相独立，互不影响。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/branch.jpeg)

### 1.11.1. 分支使用的场景

在企业开发中为了让功能快速开发完毕，往往需要多位开发同时进行编码。

假设我们需要开发一个商城，功能有商城首页、商品搜索页、重构商品详情页，你被安排编写商城首页和搜索页，而另外一位同事安排重构商品详情页，开发时间为一周。

一周后，你的首页和搜索页都开发完毕，但是另外一位同事因为家里有事只完成了 50%，这时候应用需要上线发布，要么等详情页重构完成，要么还原详情页到修改之前的状态，因为代码只编写了 50% 是没法运行的。

如果我们使用分支的技术，就没有这个烦恼了，只需要把商品首页和搜索页所在的分支代码合并到主分支即可。

### 1.11.2. 查看分支

> 命令：`git branch`

作用：查看本地所有分支，截图中`master`表示分支名字，分支前的`*`号表示当前代码所处分支。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/32.png)

### 1.11.3. 创建分支

> 命令：`git branch 分支名字`

作用：创建本地分支，创建的新分支和当前所处分支代码是一样的。截图中`dev`分支是新创建的分支，它的内容和`main`分支内容一致。

注意：分支名字可以为英文或者中文，但是一般不会使用中文作为分支名字。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/33.png)

### 1.11.4. 切换分支

> 命令：`git checkout 分支名字`

作用：切换到其他分支进行开发。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/34.png)

### 1.11.5. 创建并切换分支

> 命令：`git checkout -b 分支名字`

作用：相当于执行了`git branch 分支名字`再执行`git checkout 分支命令`这两条命令，只是用这个命令更方便，一般开发中比较常用这条命令创建分支。

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/35.png)

### 1.11.6. 删除分支

> 命令：`git branch -D 分支名字`

作用：删除分支

`注意：不能删除当前所处分支，如果要删除，需要先切换到别的分支。`

操作演示：

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/36.png)

### 1.11.7. 合并分支

> 命令：`git merge 分支名字`

作用：把分支的代码合并到当前分支。

如果合并分支和当前分支内容相同，合并时会提示`Already up to date.`

`注意：可以使用git checkout 分支名称切换到想要合并的目标分支`

演示：将 dev 分支的代码合并到 main 分支

![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/37.png)

1.12. 远程仓库相关指令
--------------

### 1.12.1. git clone 克隆远程仓库

> 作用：通过`git clone` 命令能把远程仓库代码下载到本地
> 
> 语法： `git clone 远程仓库地址`
> 
> 提供远程仓库的网站目前主要有 2 个：
> 
> 1、国外的 [www.github.com](http://www.github.com/) 网站
> 
> 2、国内的 [www.gitee.cm](http://www.gitee.cm/) 网站

举例：

```
// 把 layui这个前端库克隆到本地
git clone https://gitee.com/sentsin/layui.git


```

### 1.12.2. git remote 仓库地址做别名

> git remote 可以实现将远程仓库地址在本地做别名

*   查看所有别名
    
    ```
    语法：
    git remote
    
    
    ```
    
    ![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/41.png)
    
*   新增别名
    
    ```
    语法：
    git remote add 别名 远程仓库地址
    
    
    ```
    
    ![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/42.png)
    
*   删除别名
    
    ```
    git remote remove 别名
    
    
    ```
    
    ![](http://157.122.54.189:9092/upload/zybdoc/git/imgs/43.png)
    

### 1.12.3. git push 提交文件

> git push 命令用于将本地分支的更新，推送到远程仓库中

```
第一次提交：
git push -u 远程仓库别名 分支名称


```

注意：使用`-u`选项指定一个默认的别名，这样后面就可以不加任何参数使用`git push`来提交代码了

### 1.12.4. git pull 将远程仓库的修改更新回本地

> `git pull`命令的作用是，取回远程仓库中的某个分支的更新，再与本地的指定分支合并

```
git pull 远程仓库别名


```
### 提交代码10053错误
git提交报错信息：fatal: unable to access ‘https://github.com/*/.git/’: OpenSSL SSL_read: Connection was aborted, errno 10053
```
解决方案：在克隆完毕的仓库中将http.sslVerify设置为"false"（把忽略证书错误的设置限定在特定的仓库），命令如下：
    git config --global http.sslVerify "false"
```

### ! [rejected] master -> master (fetch first)问题的解决方案
git提交报错信息： ![](https://img-blog.csdnimg.cn/20181216111747901.png) 
```
解决方案：git提供了一种强制上传的方式：git push -f ，它会忽略版本不一致等问题，强制将本地库上传的远程库，但是一定要谨慎使用，因为-f会用本地库覆盖掉远程库，如果远程库上有重要更新，或者有其他同伴做的修改，也都会被覆盖，所以一定要在确定无严重后果的前提下使用此操作。
```

### fatal: remote origin already exists
git报错信息：fatal: remote origin already exists   
```
解决方案：由于本地的库已经连接了一个线上的仓库，如果直接连接到新远程仓库, 会报错，需要先把原来的连接删除
指令：git remote rm origin
```
