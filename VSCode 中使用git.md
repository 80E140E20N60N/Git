> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_38023551/article/details/105785223)

基本上使用
=====

在一个目录下 clone 项目；  
![](https://img-blog.csdnimg.cn/20200427104020963.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)

```
git clone XXXXXX.git

```

使用 VScode 打开项目
--------------

右击通过 Code 打开。

使用 vscode 提交代码
--------------

1.  打开下面视图，添加一行文字`## 测试提交`![](https://img-blog.csdnimg.cn/2020042710454392.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
2.  点击 + ；相当于`git add .`  
    ![](https://img-blog.csdnimg.cn/20200427104835452.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
3.  点击对号；等于`git commit -m "备注信息"`；右边的箭头输入需要备注的信息。然后按 Enter 确定。  
    ![](https://img-blog.csdnimg.cn/20200427105002367.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    回车之后，然后我们可以看到。所有的修改的文件，均已经提交到缓存区。1 变成了 0；  
    ![](https://img-blog.csdnimg.cn/20200427105443812.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
4.  提交到远程仓库；`git push origin master`  
    ![](https://img-blog.csdnimg.cn/20200427105833445.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    到 git 仓库里面；查看。已经成功提交。  
    ![](https://img-blog.csdnimg.cn/20200427110052998.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)

使用 vscode 解决冲突
--------------

在使用 git 的时候，经常会遇到冲突；这里简单的说明，如何使用 vscode 来解决冲突。  
大家在提交代码的时候，一定要先**拉取代码**；不然就会造成冲突；

1.  拉取代码 `git pull origin master`  
    ![](https://img-blog.csdnimg.cn/20200427110535952.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    这里说明一下造成冲突之后，如何处理。下面是同一个项目，放到不同的文件下面。在未拉取代码的情况下，对文件进行修改的操作。造成冲突的解决方式。  
    ![](https://img-blog.csdnimg.cn/20200427110729287.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
2.  增加一句话`我是修改`  
    ![](https://img-blog.csdnimg.cn/20200427111236901.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
3.  提交代码  
    ![](https://img-blog.csdnimg.cn/20200427111435570.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    ![](https://img-blog.csdnimg.cn/20200427111536207.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    回车，enter；提交到远程仓库。  
    ![](https://img-blog.csdnimg.cn/2020042711165444.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
4.  提交到远程仓库的时候，这时候会报错  
    ![](https://img-blog.csdnimg.cn/20200427111806356.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
5.  拉取远程代码  
    ![](https://img-blog.csdnimg.cn/20200427111911489.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    结果如下，显示出冲突的文件  
    ![](https://img-blog.csdnimg.cn/20200427112007969.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    这里有几个操作来进行快速的修改。  
    ![](https://img-blog.csdnimg.cn/20200427112124336.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    我这里选择的 **保留双方的更改**；然后结果如下。  
    ![](https://img-blog.csdnimg.cn/20200427112222957.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
6.  重新提交代码。  
    ![](https://img-blog.csdnimg.cn/20200427112454561.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    放到缓存区  
    ![](https://img-blog.csdnimg.cn/20200427112534886.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    推送到远程仓库  
    ![](https://img-blog.csdnimg.cn/20200427112622385.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)
7.  查看结果  
    ![](https://img-blog.csdnimg.cn/20200427112725358.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)  
    现在  
    ![](https://img-blog.csdnimg.cn/20200427112816682.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODAyMzU1MQ==,size_1,color_FFFFFF,t_70)