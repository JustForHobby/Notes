# idea创建git项目并提交到github上

最近在学习SpringBoot，用的IDEA进行开发，所以就想试着，将学习的小案例分享到GitHub上，希望我写的这个方法可以帮助到你！

前提：

- 你已经有了Github账号并且已经完成基本设置，而且会在Github中创建仓库等基本操作，没有的话去注册，不会设置的可以参考我的另外两篇博文：（1）https://my.oschina.net/aibinxiao/blog/913678；（2）https://my.oschina.net/aibinxiao/blog/913600
- 你已经在本机安装了Git客户端；
- 你用的IDEA；

工具版本：

- Git客户端：Git-2.10.0-64-bit
- IDEA：ideaIU-2016.2.5

现在正式开始：

1. 用IDEA打开需要上传到Github的项目，创建一个本地git仓库，默认路径是项目文件夹存放路径；操作：点击CVS--->选择import into Version Control--->点击Create Git Respository![img](https://static.oschina.net/uploads/space/2017/0605/135235_Lgpi_2931098.png)

2. 点击Create Git Respository之后，选择目录，即选择项目文件夹即可，如图所示：![img](https://static.oschina.net/uploads/space/2017/0605/135417_jL5H_2931098.png)

3. 点击OK之后，该项目下的所有文件都会变成红色的，如图所示：![img](https://static.oschina.net/uploads/space/2017/0605/135458_iHxj_2931098.png)

4. 右键单击该项目，选择Git--->点击+Add，然后该项目所有文件变成绿色，如图所示：![img](https://static.oschina.net/uploads/space/2017/0605/135821_WWhX_2931098.png)![img](https://static.oschina.net/uploads/space/2017/0605/135723_R3qF_2931098.png)

5. 右键单击该项目，选择Git--->点击提交到本地Git。如图所示：![img](https://static.oschina.net/uploads/space/2017/0605/140011_IuAw_2931098.png)

6. 点击Commit Directory后，需要你选择需要提交的文件和注释，首次默认选中全部文件，注释最好写上，方便日后查看，确认无误后，点击commit，如图所示：![img](https://static.oschina.net/uploads/space/2017/0605/140435_8SSn_2931098.png)

7. 接下来只需要将本地的git项目上传到Github中创建好的仓库中。进入项目所在文件夹，右键单击---点击Git Bash here，依次输入命令：

   ```
   git remote add origin {Github中创建的repository的url}
   ```

   ```
   git pull origin master
   ```

   

   当输入git pull origin master后，出现错误：fatal:refusing to merge unrelated histories，意思是拒绝合并不相关的历史，这是因为在Github创建仓库时，我默认创建了README.md和LICENSE两个文件，而本地是没有的，所以出现冲突了，这时候，我们需要将第2条命令改为：

   ```
   git pull origin master --allow-unrelated-histories
   ```

   注意：输入完上面这条命令后，这时候会进入一个Vim编辑器，让你写为什么要合共这两个不相关的历史文件，这时候你只要输入原因，然后--->Esc--->输入：wq即可退出。

   

   在退出Vim的编辑模式后，你会看到如下信息，即成功合并了Github中已经存在的两个文件：

   

   注意“.”表示上传文件夹中的所有文件

   ```
   git add .
   ```

   ```
   git commit –m "上传项目到Github"
   ```

   ```
   git push {Github中创建的repository的url}
   ```

   经过一段时间的执行上面最后一条命令后，你会看到如下：

   

8. 最后，你回到Github中刷新页面，就可以看到刚刚提交的项目，恭喜你这个时候，你就成功的将本地git中的项目同步到了Github中了！如图所示：![img](https://static.oschina.net/uploads/space/2017/0605/145203_cIz9_2931098.png)

 

本文为原创文章，如果对你有一点点的帮助，别忘了点赞哦！比心！如需转载，请注明出处，谢谢！

 