# SAS云使用教程

SAS官方对没有安装SAS环境的程序员们，提供了部署在SAS私有云上的SAS Studio开发环境，可以让大家随时随地免费使用，编写/运行SAS代码，所有的数
据和代码都会存储在SAS私有云！这是目前学习SAS程序开发成本最低、最快捷的方法。

![Alt text](/png/sas studio.png)

## 1.注册用户

在浏览器中输入网址：https://www.sas.com/profile/ui/#/create ，提交用户名来注册
账号，你的邮箱将会收到用户ID，该用户ID会在后面用来登陆SAS Studio

![Alt text](/png/注册.png)

## 2.登录云端

注册完成后，通过网址 https://odamid.oda.sas.com/SASStudio 登录SAS Studio。此时需要您的【用户ID】和【用户密码】。注意：这儿的【用户ID】 并非你的邮箱地址，而是系统给你分配的用户ID。其界面如下：

![Alt text](/png/登录.png)

目前提供服务的SAS Studio 为3.7 企业版，支持Chrome27+，IE9-11, Firefox 21+ 和 Apple Safari 6.0+ 以上的浏览器。后台SAS为Linux 64位版本。

SAS Studio 为用户提供一个编写/执行SAS程序、简便高效的Web开发环境。


## 3.开发程序

登录SAS Studio后，其主界面包括上面的菜单栏、左侧的导航面板和右侧的内容窗口，
导航面板“服务器文件和文件夹”、“任务和实用程序”、“代码段”、“逻辑库”、“文件快捷方式”
 和 “SAS文件夹” 等内容。其中“服务器文件和文件夹”和“逻辑库” 比较常用。服务器文件和文件夹是你在服务器上的磁盘空间，一般映射到你的主目录/home/yourid/上。

![Alt text](/png/登录2.png)

右侧提供了程序窗口，包括 “代码”，“日志“ 和 “结果” 三个窗口。一般步骤是在代码窗口中输入SAS程序，然后点击代码页签工具栏最左边的运行按钮、或者直接按键盘上F3功能键直接执行代码。比如：

执行结果可以查看日志窗口，比如：

```python
data circle;
  pi=3.141593;
  do i=1 to 2*pi by 0.01;
    x=sin(i);
    y=cos(i);
    output;
  end;
 RUN;
 proc print data=circle;
 run;
```
![Alt text](/png/程序1.png)
![Alt text](/png/程序1.1.png)


在分析中你可能需要上传自己的数据文件，你可以右键点击左侧导航面板中的 “文件（主目录）”，然后在菜单中选择 “上载文件…”

![Alt text](/png/程序2.png)

在如下弹出对话框中选择 “选择文件”，然后选择你本地电脑上的数据文件，比如c:\temp\toBuildModel.csv ，即可将文件上传到您的服务器上。

上传完毕在左侧的导航面板“文件（主目录）”中将出现 toBuildModel.csv 文件，表明该文件已经传到云端。
如果要将该csv数据导入到SAS 系统中，我们可以双击它，SAS Studio会自动给您生成对应的SAS Code来导入数据。
你也可以选择不同的参数来进行数据导入。(默认导入到了work.import)

![Alt text](/png/程序3.png)

如果我们上传一个本地 Windows 导出的csv文件（中文 Windows环境上生成的中文数据默认是GB2312编码），而在SAS导入的时候会默认为我们上传的是 UTF-8 格式的文件，此时就会出现乱码的情况。解决方法是：

a) 我们手工用记事本或其他工具将数据文件转码；

b）如果我们是 Windows 导出的 csv 文件，需要指定数据源文件是 gb2312。在双击toBuildModel.csv文件后，点击右下角的 “编辑”，SAS Studio会自动给你生成新的SAS代码 “程序2”。运行即可正确导入数据。

![Alt text](/png/程序4.png)

在结果窗口中可以看到导入完毕的数据，比如数据集名称 WORK.IMPORT。缺省情况下输出数据都会放在临时逻辑库 WORK 中。

![Alt text](/png/程序4.4.png)

由于 WORK 是临时逻辑库，在SAS会话结束时系统会自动删除。如果我
们要在服务器磁盘上永久保存该临时导入的数据集 WORK.import，我们可以在导入之前指定一个非临时逻辑库来保存数据、或者如下：我们新建一个逻辑库 mylib ，然后在 mylib 中生成一份WORK.CLASS的拷贝。如下：

```python
libname mylib “/home/n26034612340/mylib”;

data mylib.toBuildModel;
   set work.import;
run;
```

运行上面的代码后，我们可以看到服务器的“逻辑库/我的逻辑库” 中多了 MYLIB，其中还包括数据 toBulidModel。

![Alt text](/png/程序5.png)

同时也在服务器上编写完了SAS 程序后，我们就可以随时注销，关闭SAS Studio 应用了，鼠标点击右上角的 “注销” 菜单即可。

![Alt text](/png/注销.png)

由于所有数据都保存在云端，因此你下次登录时所有的数据和程序都还在，你可以随时继续你的分析工作… 也可以随时保存工作并退出！
