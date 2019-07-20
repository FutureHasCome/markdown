# 什么是SAS云

## 1.什么是SAS以及为什么要用SAS

SAS(Statistical Analysis System,简称SAS)是一个（大）数据分析、风险管理模型、商业智能等领域的大型统计分析软件，由美国北卡罗来纳周立大学于
1966年开发，现广泛服务于金融电信、政府、制造、零售、医疗等各大行业，在高级分析及预测分析领域全球第一。据统计，在《财富》全球500强中大约91%
的公司均采用SAS软件，其中包括了多家银行和大型保险公司。

SAS功能强大，统计方法齐全，分析技术先进可靠，并且使用简单操作灵活。尽管目前SAS在国内的影响力有限，但对于想出国的同学或进入外企工作的同学来说，
掌握SAS将是一个优势。

![Alt text](/png/saslogo.jpg)

SAS包含了多个工具模块，其模块按功能大体有四类
+ 数据库部分：BASE,FSP,ACCESS,..
+ 分析核心：STAT,ETS,QC,OR,INSIGHT
+ 开发呈现工具：AF,EIS,GRAPH,...
+ 分布处理与数据仓库：CONNECT,WA,..

Base SAS作为SAS系统的核心，负责数据管理，交互应用环境管理，调用其它SAS模块，进行用户语言处理等。Base SAS为SAS系统的数据库提供了丰富的数据管理
功能，并支持标准的SQL语言对数据进行操作；Base SAS可进行基本的描述性统计，进行正态分布检验等；并能制作复杂的统计报表。本文也将重点介绍该模块的使用

## 2.一些简单的应用

+ 分配一个逻辑库引用名

可以通过使用LIBNAME语句为一个SAS逻辑库分配引用名，但逻辑库名不能超过8个字符，必须以字母或下划线开头，其余字符必须是字母，数字或者下划线。

```python
libname saslib 'd:\sas';
```

+ sas注释

sas注释是指sas在处理过程中忽略的文本，可以在程序的任何位置使用注释以记录该程序的目的

多行注释 /*comment*/
```python
/*
proc print data=work.NewSalesEmps;
run;
*/
```

单行注释  *comment;
```python
proc means data=work.NewSalesEmps;
  *class Job_Title;
  var Salary;
run;```
+ 浏览数据部分

print过程显示一个SAS数据集的数据部分，包括所有观测、变量,这里的work是临时逻辑库，data1是逻辑库work里的数据集

```python
proc print data=work.data1;
run;```

+ 创建SAS数据集,不指定逻辑库时，tem的逻辑库就是临时逻辑库work

```python
data tem;
  infile datalines;
  input date $1-7 dest $8-10 num 11-13;
  datalines;
01MAR90LON198
02MAR90FRA207
03MAR90LON205
  ;
run;
proc print;
run;```




+ 简单程序：计算根号3,程序提交后将在日志窗口给出结果为y=1.73205....

```python
data _null_;
  y=sqrt(3);
  put y=;
run;```

+ 读取Excel文件建立SAS数据集

将存储在d:\data目录下的excel文件data1.xls中的数据导入，并放在逻辑库saslib的data1数据集中
并将excel文件中第一行作为变量名导入

```python
proc import out=saslib.data1;
  datafile="d:\data\data1.xls"
  dbms=excel replace;
  getnames=yes;
run;
```

+ 选择观测-IF语句

```python
data a;
  set old;
  if sex="F"; /*保留sex为F的观测*/
  /*where sex="F";也可以达到同样的效果*/
run;
```
```python
data a;
  set old;
  if sex="M" then delete; /*删除sex为M的观测*/
run;
```

+ 选择变量keep/drop语句

```python
data a;
  set old;
  keep name height weight; /*保留变量name height weight*/
run;```

```python
data a;
  set old;
  drop sex age; /*删除变量sex age*/
run;```
+ 循环输出立方表

这里的步长为2，可以输出一个1,3,5,7，...19的立方表，可以用leave语句跳出循环

```python
data _null_;
  do i=1 to 20 by 2;
    j=i**3;
    put i 3. j 5.;
  end;
run;
```

+ 使用数组进行变量的循环处理

读入了comp1-comp10是个计算机销售额变量，prin1-prin6六个打印机销售额变量，希望计算其总和，可以用如下的数组说明和DO循环配合进行

```python
data sales;
  input comp1-comp10 prin1-prin6;
  array y(*) comp1-comp10 prin1-pin6;
  tot=0;
  do i=1 to dim(y);
    tot+y(i);
  end;
  cards;
run;
```
+ 合并SAS数据集

```python
data combine;
  set c d; /*纵向合并c d两个sas数据集*/
  by num;  /*按照num进行升序排序*/
run;
```
```python
data combine;
  merge a b; /*横向合并c d两个sas数据集*/
  by num;  /*按照num进行连接，全连接*/
run;
```
+ SAS作图

使用SAS画圆

```python
DATA circle;
  pi=3.141593;
  do i=1 to 2*pi by 0.01;
    x=sin(i);
    y=cos(i);
    output;
  end;
 RUN;
 PROC GLPOT data=circle;
  plot x*y;
 RUN;
```
+ 使用SQL语句

sas中使用的sql语句是标准sql语句

```python
  proc sql;
    select *
    from saslib.data1
    where sex="F";
  quit;
```


## 3.获取SAS软件的途径

+ 学校官网获取正版软件

不少高校从SAS公司购买了学院版SAS软件，可以供本校老师和学生在教学和科研中使用。在学院官网下载好SAS软件，再申请使用licsense，即可获取授权

![Alt text](/png/学院官网.png)
+ 购买正版软件

这个方法就比较贵了，SAS软件按年来收取费用，价格不菲，个人版SAS软件达到上万元，并不适合学生党使用，一般大型公司才会集体采购SAS软件
详见SAS官网 https://support.sas.com/en/support-home.html

![Alt text](/png/sas官网.png)
+ 某宝购买

学生党一般会建议去某宝店看看，某宝店会提供安装包、下载教程，更新的Liecense文件，服务算是比较周到，价格
也还能接受（如果你能顺利从某网盘下完10G+的安装包）。

![Alt text](/png/淘宝.jpg)
+ SAS私有云

SAS官方对没有安装SAS环境的程序员们，提供了部署在SAS私有云上的SAS Studio开发环境，可以让大家随时随地免费使用，编写/运行SAS代码，所有的数
据和代码都会存储在SAS私有云！这是目前学习SAS程序开发成本最低、最快捷的方法。
关于SAS Studio的介绍及使用将在次条进行详细的介绍

![Alt text](/png/sas studio.png)
## 4.SAS书籍推荐

+ 《The little SAS book》
+ 《Learning SAS by example》
+ 《深入解析SAS-数据处理、分析优化与商业应用》
+ 《A Handbook of Statistical Analyses Using SAS 3rd》
+ 《统计软件教程》
+ 《SAS编程与数据挖掘商业案例》

sas官方教材：

![Alt text](/png/sas官方教材.png)
