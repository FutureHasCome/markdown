## 第一课：C++简介

> 学习了helloworld程序以及一些简单的知识点

```c++
//hello world

#include <iostream>

using namespace std;
int main()
{
  cout <<"Hello World !!!" <<endl;
  return 0;
}
```

**命名空间**：using namespace std  
感觉会比较像Java的import com.io.iostream的形式

**打印语句** cout (charchater out)  
&lt;&lt; 就像流水一样流出到cout对象，插入

**endl的作用**  

1.换行，和“\\n”的作用一致  
2.立即输出的作用

**C++程序的执行过程**  

先加载预处理的文件，比如iostream，然后编译成汇编文件，再汇编成二进制文件，最后和C++函数库进行链接，生成可执行的exe文件执行。

## 第二课：变量及数据类型

**变量**

内存：也称为主存（寄存器），或随机访问存储器（Random Access Memory,RAM),计算机执行程序时，组成程序的指令和程序所操作的数据都必须存放在内存。

五行八卦的八卦就是八进制？  
bin目录就是二进制文件，里面有exe，就是电脑可以执行的文件

变量是计算机中一块特定的内存空间，由一个或多个连续的字节组成  
不同数据存入不同内存地址的空间，相互独立  
通过变量名可以简单快速地找到在内存中存储的数据

8 bit 比特=1 byte 字节  0和1
10M bps =10M bit per second

C++语言变量命名规则和JAVA差不多  

1.  首字母只能是\_或字母

2.  不能是关键字

3.  \_ 字母 数字 ，不能有% # 逗号，空格等

4.  不要使用拼音和单个英文单词，提倡使用有正式含义的英文单词

**常用的数据类型**

1.  数值型

    整型 Int 32bit 4byte  
    (32bit的二进制也就是2^31+2^30+...+2^0，也就是2^32-1)  
    整形 short 16bit 2byte  
    整形 long 32bit 和int的长度一样

    单精度浮点数 float 32bit  
    双精度浮点数 double 64bit

    字符型 char 8bit -128~+127,用于存储单个字符

    布尔类型 bool

    长整型 long long 64bit

2.  非数值

    String类型

注意：还有无符号版，与有符号版的区别是什么？
还有size_t类型、枚举类型、自定义类型、指针类型、空类型等

```c++
//这个代码无法运行，喵喵喵
#include <climits>
#include <iostream>
using namespace std;

int main() {
	//cout << "Hello World!!!" << endl; // prints Hello World!!!
	cout << LONG_MAX << endl;
	return 0;
}
```

推荐的命名方式：  
wife_name  
wifeName

```c++
#include <iostream>
using namespace std;

int main() {
  //这个是无符号版的int
	size_t abc=19;
  cout << abc <<endl;

  //可以取一个别名
  typedef char myChar;
  myChar defg='a';
  cout << defg <<endl;

	return 0;
}
```

**输入输出**

```c++
#include <iostream>
using namespace std;

int main() {
  //打印整形
  int salary=2000;
  cout << "小明同学的月薪：" << salary <<endl;

  int num = 1, num2 = 8;
  cout << num1 << "思君思国思社稷\n";
  cout << num2 << "赏花赏月赏秋香" <<endl;

  //或者只用一个count
  cout << num1 << "思君思国思社稷\n";
       << num2 << "赏花赏月赏秋香" <<endl;

	return 0;
}
```

float 的有效数字只有6-7位，比如12345.123457打印出来就是12345.1

```c++
#include <iostream>
#include <cmath>
using namespace std;

int main() {

  float num=12345.1234567;
  cout << num << endl;

  //计算圆柱体的体积
	const float pi=3.14f;  //定义常量
	float radius=4.5f;
	float height=90.0f;
	double volume=pi * pow(radius,2) * height;
	cout << "圆柱体的体积是：" << volume <<endl;
	return 0;
}
	return 0;
}
```

cin/cout练习：加上了数据类型/变量的输出

```c++
#include <iostream>
#include <windows.h> //控制台的标题
using namespace std;

int main() {

	//改变控制台的标题,不过使用eclipse编译器看不出来哎
	SetConsoleTitle("德玛西亚之力");

	//打印德玛西亚之力

	/* 攻击伤害值 */
	double value_attack = 158.88;
	/* 攻击伤害增长值 */
	double value_attack_growth = 3.5;

	/* 防护值*/
	double value_defence = 203.88;
	/* 防护值增长值 */*/
	double value_defence_growth = 3.5;

	cout << "德玛西亚之力" << endl;
	cout << "攻击伤害值：" << value_attack <<"(+" << value_attack_growth << ")\t"
	     << "攻击伤害值：" << value_defence <<"(+" << value_defence_growth << ")" << endl;
	return 0;
}
```

//这也是一个cin/cout的实例，尤其是cin如何接受输入

```c++
//用于写C++程序的地方

//例子：cin/cout的实例
#include <iostream>

using namespace std;
int main()
{
  int num;
  char ch1,ch2,ch3;
  //1.当输入123abc的时候，打印出来的就是123 a,因为char只能存放单个字符
  cout << "请输入：" << endl;
  cin >> num;
  cin >> ch;
  cout << num << "\t" << ch << endl;

  //2.此时打印出来的就是123 a b c
  cout << "请输入：" << endl;
  cin >> num;
  cin >> ch1 >> ch2 >> ch3;
  //不过最好建议以下面的方式书写
  //ch1=cin.get();
  //ch1=cin.get();
  cout << num << "\t" << ch1 << "\t" << ch2 << "\t" << ch3 << endl;
  return 0;
}
```

* * *

**如何在ATOM执行代码时使用中文**  
把右下角的utf-8改成gbk后再开始码代码，然后再控制台就可以输出正确的中文了。

* * *

// 如何控制输出的格式，比如说左对齐右对齐，宽度啊，填充啊，保留的小数点位数啊

```c++
//例子：cin/cout的实例
#include <iostream>
#include <iomanip> //io代表输入输出,manip是manipulator(操纵器)的缩写
using namespace std;
int main()
{
  //如何设置输出的宽度
  int num1 = 123;
  int num2 = 345;
  int num3 = 567;

  cout << left; //设置左对齐
  cout << setfill('*');//设置不足8位的其他位的填充,必须要用单引号才可以？
  //默认是右对齐
  cout << setw(8) << num1
       << setw(8) << num2
       << setw(8) << num3 << endl;
  return 0;
}
```

**算术运算符**

1.讨论了除、余的区别；  

2.++与--前置后置的区别；

3.讨论了取余的符号问题

```c++
//例子：算术运算符
#include <iostream>
using namespace std;
int main()
{
  //除和取余
  int num1 = 5;
  int num2 = 2;
  cout << num1 / num2 << endl; //输出的是2
  cout << num1 % num2 << endl; //输出的是1

  //当都是浮点数的时候，除得到的也就是浮点数
  double num3 = 5;
  double num4 = 2;
  cout << num3 / num4 << endl; //输出的就是2.5了

  //可以知道取模的话，符号由第一个数的符号决定的
  int num11 = 5;
  int num21 = -5;
  int num31 = 2;
  int num41 = -2;
  cout << num11 % num31 << endl; //输出的是1
  cout << num11 % num41 << endl; //输出的是1
  cout << num21 % num31 << endl; //输出的是-1
  cout << num21 % num41 << endl; //输出的是-1

  // ++和--的区别和应用
  // ++x 是先对x=x+1，再用来计算表达式
  // x-- 是先用x计算表达式，再x=x-1
  num2 = 2;
  int num5 = num2++ - --num2;
  //num5的值是0,num2的值是2
  cout << "num5:" << num5 << "\t" << "num2:" << num2 << endl;

  /*1.num2++ = num2 = 2;
    2.num2 = num2 + 1 = 3;
    3.--num2 = num2 - 1 = 2;
    4.num2 = num2 -1 =2;
    5.num2++ - --num2 =0;
  */*/

  int a = 20;
	int b = 20;
  // a=20,b=20
	cout << "a=" << a << ":b=" << b << endl;
  //a++=20,++b=21;
	cout << "a++=" << a++ << ":++b=" <<++b << endl;
  //a=21,b=21
	cout << "a=" << a << ":b=" << b << endl;
  return 0;
}
```

**类型转换**

原则：
1.把表示范围小的类型的值自动转换到表示范围大的类型的值
short-> int -> long -> float -> double

2.强制转换，（类型名）变量或数值

```c++
//例子：类型转换
#include <iostream>
using namespace std;
int main()
{
  //类型转换
  int num1 = 5;
  int num2 = 2;
  double result=num1 / num2;
  cout << "The Value of Result is :" << result << endl; //输出的是2

  return 0;
}
```

## 3. 循环控制

cstdlib标准库常用函数：  

    1.rand函数：用于产生随机数

    2.srand函数：用于初始化随机数种子

    3.system函数：用于DOS系统功能调用

    4.exit函数：用于退出程序

    5.qsort函数：快速排序

    6.itoa、atoi、atof等一系列转换函数

    7.malloc函数：（也可以用头文件malloc.h）动态分配内存

ctime:定义了获取和操作日期和时间的函数

```c++
//用于写C++程序的地方

//例子：类型转换
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;
int main()
{
  //while循环,和JAVA差不多的
  int i = 0;
  while (i <= 10)
  {
    cout << "This is the " << i << " times" << endl;
    i++;
  }
  //这里的不是判断，而是赋值，相当于了while(1)，会一直循环下去的
  /*int j = 0;
  while(j = 1)
  {
    cout << "j = " << j << endl;
  }*/

  //在while中使用随机数种子
  //循环变量
  int m = 1;
  //起始分数
  int little_red = 10;
  int little_blue = 10;
  //设置随机数种子，随着时间改变,感觉用时间做随机数不太平衡啊
  srand( time(NULL) ) ;
  while(m <= 100)
  {
    if(rand() % 2 == 0) //奇数  //rand()可以产生随机数.不需要参数，0到最大随机数的任意整数
    {
      // +=号就是，先将该符号左边的值加到右边值后，再将其复制给左边的
      little_red += 8;
      little_blue -= 5;
    }else
    {
      little_blue += 8;
      little_red -= 5;
    }
    m++;
  }
  cout << "The score of little_red : " << little_red << endl;
  cout << "The score of little_blue : " << little_blue << endl;
  cout << "The maximum of rand: " << RAND_MAX << endl; //居然是32767
  return 0;

}
```

do while循环

```c++
//例子：do while 循环
#include <iostream>
using namespace std;
int main()
{
  //while循环,和JAVA差不多的
  int a = 1, b = 10;
  do {
    b -= a;
    a ++ ;
  } while(b-- < 0);  //
  cout << "b = " << b << endl; //可以得到b=8
  return 0;
}
```

## 第四课 数组及常用算法

数组：就是一个变量，由数据类型相同的一组元素组成  
变量：内存中的一块空间  
数组：内存中的一串连续的空间

下标为什么要从0开始？

198 98 'c' 230 是一个合理的整形数组，因为char类型就是以数字来表示的  
1 0 true false 38 -1 这个数组也是可以的

```c++
//例子：数组
#include <iostream>
using namespace std;
int main()
{
  //char字符
  int a[] = {198, 98, 'c', 230};
  cout << "a[2] = " << a[2] << endl; //可以得到a[2]=99;

  //布尔类型
  int b[] = {1, 0, true, false, 38, -1};
  cout << "b[2] = " << b[2] << endl; //可以得到b[2]=1;
  return 0;

}
```

数组定义的一些注意事项：

```c++
//例子：数组
#include <iostream>
using namespace std;
int main()
{
  //定义数组
    //1.使用常量定义长度是可以的；
  const int N=100;
  int num[N];
  num[0]=100;
    //2.使用变量定义长度也是可以的；
  int n=100;
  int num1[n];
  num1[0]=100;
  cout << "num[0] = " << num[0] << endl;
  cout << "num1[0] = " << num1[0] << endl;

  //初始化一维数组，可以少给但是不能多给
  //后面5个元素未初始化，默认值为0
  int months[12]={1, 3, 5, 7, 8, 10, 12};
  cout << "months[10] = " << months[10] << endl; //months[10]=0;

  //先不给定长度也是可以的，系统自动计算数组的长度；
  int days[]={1, 15};
  //是可以不写等于符号的哟
  int days1[]{1,15};
  //大括号可为空，所有元素置零
  float m[100]{};

  return 0;

}
```

动态赋值给数组

```c++
//例子：数组
#include <iostream>
using namespace std;
int main()
{
  //动态赋值给数组，C++没有num.length
  const int N=5;
  int num[5];
  //sizeof(num)=20;总共20个字节，一个Int4个字节，就可以算出数组的长度
  cout << "sizeof(num) = " << sizeof(num) <<endl;

  //sizeof(int)=4;int是四个字节，也就是32位
  cout << "sizeof(int) = " << sizeof(int) <<endl;
  //这种只适合基本类型，double类型、float类型就不一定
  for(int i = 0; i <  sizeof(num) / sizeof(int); i++)
  {
    cout << "请输入第" << (i+1) << "个元素的值：" << endl;
    cin >> num[i];
  }
  for(int i = 0; i < N; i++)
  {
    cout << num[i] << "\t";

  }

  return 0;

}
```

数组的练习

```c++
//例子：数组练习
#include <iostream>
#include <climits>
using namespace std;
int main()
{
  //1.求数组中的最大值和最小值
  cout << "1.求数组中的最大值和最小值" << endl;
  int num[] = {10,20,30,45,12,89,45};
  //求出组数的长度
  int numsLen = sizeof(num) / sizeof(int);
  //声明最大最小值变量
  int min = num[0];//int min=INT_MAX;
  int max = num[0];//int max=INT_MIN;

  for(int i = 1; i < numsLen; i++)
  {
    if(num[i] < min)
    {
      min=num[i];
    }
    if(num[i]>max)
    {
      max=num[i];
    }
  }
  cout << "max = " << max << endl;
  cout << "min = " << min << endl;

  //定义一个整型数组，赋值后求出奇数个数和偶数个数
  cout << endl;
  int num_of_jishu = 0;
  int num_of_oushu = 0;
  cout << "2.定义一个整形数组，赋值后求出奇数个数和偶数个数" << endl;
  for(int i = 0; i < numsLen; i++)
  {
    if(num[i] % 2 ==0) //偶数哟
    {
      num_of_oushu++;
    }
    else
    {
      num_of_jishu++;
    }
  }
  cout << "num_of_oushu = " << num_of_oushu << endl;
  cout << "num_of_jishu = " << num_of_jishu << endl;

  //查找输入的数字在数组中的下标，没有找到则下标为-1
  cout << endl;
  cout << "3.查找输入的数字在数组中的下标，没有找到则下标为-1" << endl;
  //用户输入的数字
  int user_num;
  //下标
  int index = -1;
  cout << "请输入想要查找的数字：" << endl;
  cin >> user_num;
  for(int i = 0; i < numsLen; i++)
  {
    if(user_num == num[i])
    {
      index = i;
      break;
    }
  }
  cout << "index = " << index << endl;
  return 0;

}
```

## 数组排序

-   冒泡排序  
    第一轮比较的次数：n-1;  
    第二轮比较的次数：n-2;


```c++
#include <iostream>
using namespace std;
int main()
{
  //数组排序
  int num[] = {15, 25, 90, 23, 9, 59, 21};  //定义的数组
  int numsLen = sizeof(num) / sizeof(int); //数组的长度
  //1.冒泡排序降序输出
  cout << "1.冒泡排序降序输出" << endl;
  //开始冒泡泡
  //外层循环控制比较的轮数
  for(int j = numsLen - 1; j > 0; j--)
  {
    //内层循环控制每轮的比较和叫魂
    for(int i = 0; i < j; i++)
    {
      if(num[i] < num[i + 1])
      {
        //交换
        int temp = num[i]; //int temp写在外面也可以
        num[i] = num[i + 1];
        num[i + 1] = temp;
      }
    }
  }
  for(int i = 0; i < numsLen; i++)
  {
    cout << num[i] << "\t";
  }

  //2.冒泡排序降序输出
  cout << endl;
  cout << "2.冒泡排序升序输出" << endl;
  for(int j = 0; j < numsLen - 1; j++)
  {
    //内层循环控制每轮的比较和叫魂
    for(int i = numsLen-1; i > j; i--)
    {
      if(num[i] < num[i - 1])
      {
        //交换
        int temp = num[i]; //int temp写在外面也可以
        num[i] = num[i - 1];
        num[i - 1] = temp;
      }
    }
  }
  for(int i = 0; i < numsLen; i++)
  {
    cout << num[i] << "\t";
  }

  //3.使用选择排序升序
  cout << endl;
  cout << "3.选择排序升序输出" << endl;
  //外层控制循环
 for(int i = 0; i < numsLen - 1; i++)
 {
  //内层循环控制
  for(int j = i+1; j < numsLen-1; j++)
  {
    if(num[j] < num[i])
    {
      int temp = num[i];
      num[i] = num[j];
      num[j] = temp;
    }
  }
 }
 for(int i = 0; i < numsLen; i++)
 {
   cout << num[i] << "\t";
 }

 //使用选择排序降序
 cout << endl;
 cout << "4.选择排序降序输出" << endl;
 //外层控制循环
for(int i = 0; i < numsLen - 1; i++)
{
 //内层循环控制
 for(int j = i+1; j < numsLen; j++)
 {
   if(num[j] > num[i])
   {
     int temp = num[i];
     num[i] = num[j];
     num[j] = temp;
   }
 }
}
for(int i = 0; i < numsLen; i++)
{
  cout << num[i] << "\t";
}

}
```
数组插入删除

```c++
//例子：数组的删除/插入
#include <iostream>
using namespace std;
int main()
{
  //实现数组元素的删除和插入
  //c++也是没有动态数组的
  double power[99];//数组的大小一旦确定了，就不能更改了！
  int powerCount = 0;//当前数组中的元素个数
  power[powerCount++] = 45771;
  power[powerCount++] = 45568;
  power[powerCount++] = 86577;
  power[powerCount++] = 89771;
  double insertPower;
  int insertIndex = powerCount;//默认的插入位置
  double deletePower;
  int deleteIndex = -1;

  double temp;
  //选择排序
  for(int i = 0; i < powerCount - 1; i++)
  {
    for(int j = 0; j < powerCount - i - 1; j++)
    {
      if(power[j] < power[j+1])
      {
        temp = power[j];
        power[j] = power[j+1];
        power[j+1] = temp;
      }
    }
  }
  cout << "排序后：" << endl;
  for(int i = 0;i < powerCount; i++)
  {
    cout << power[i] << "\t";
  }

  cout << endl;
  cout << "请插入要插入的数字：";
  cin >> insertPower; //保证数组仍然是有序的
  //找到第一个比插入数字小的位置insertIndex
  for(int i = 0; i < powerCount; i++)
  {
    if (power[i] < insertPower)
    {
      insertIndex = i;
      break;
    }
  }
  //从后面一个元素开始，将数字复制到后一个元素中
  for(int i = powerCount; i > insertIndex; i--)
  {
    power[i] = power[i-1];
  }
  //将要插入的数字赋值给下标为insertIndex的元素
  power[insertIndex] = insertPower;
  powerCount++;
  cout << endl;
  cout << "插入数据后：" << endl;
  for(int i = 0;i < powerCount; i++)
  {
    cout << power[i] << "\t";
  }

  //删除


  cout << endl;
  cout << "请输入要删除的数字：";
  cin >> deletePower;
  //1.要找到要删除的元素下标
  for(int i = 0; i < powerCount; i++)
  {
    if(power[i] == deletePower)
    {
      deleteIndex = i;
      break;
    }
  }
  //2.从找到的元素下标开始，当前值等于后一个的值
  if(deleteIndex < 0)
  {
    cout << "您要删除的数据" << deletePower << "不存在" << endl;
  }
  else
  {
    for(int i = deleteIndex; i < powerCount; i++)
    {
      power[i] = power[i + 1];
    }
    //总长度-1
    powerCount--;
  }
    cout << "删除数据后：" << endl;
    for(int i = 0;i < powerCount; i++)
    {
      cout << power[i] << "\t";
    }

}
```

## 二维数组

```c++
//例子：二维数组
#include <iostream>
using namespace std;
int main()
{
  string stuNames[]{"刘备", "关羽", "张飞"};
  string courseNames[]{"语文", "数学", "英语"};
  const int ROW = 3;//sizeof(stuNames) /sizeof(stuNames[0]);
  const int COL = 3;//sizeof(courseNames) /sizeof(courseNames[0]);

  double scores[ROW][COL];
  //输入学生的各科成绩
  for(int i =0; i < ROW; i++)
  {
    for(int j = 0;j < COL; j++)
    {
      cout << stuNames[i] << "的" << courseNames[j] << "成绩: ";
      cin >> scores[i][j];
    }
  }
  //打印学生各科的成绩
  cout << endl;
  cout << "\t";
  for(int j = 0;j < COL; j++)
  {
    cout << courseNames[j] << "\t";
  }
  cout << endl;
  for(int i =0; i < ROW; i++)
  {
    cout << stuNames[i] << "\t";
    for(int j = 0;j < COL; j++)
    {
      cout << scores[i][j] << "\t";
    }
    cout << endl;
  }
  return 0;
}
```

## 数组的替代品--向量容器vector
vector 是一个快速的动态分配内存的数组  
+ 动态数组，可以在运行阶段设置长度  
+ 具有数组的快速索引方式  
+ 可以插入和删除元素

**定义和初始化：**
vector<double> vec1;  
vector<string> vec2(5);
vector<int> vec3(20,998); //20个元素，每一个都是998;  

**常用操作**
+ clear()  移除容器中的所有数据
+ empty()  判断容器是否为空
+ size()   返回容器中元素的个数
+ [index] at(index) 返回索引为index的元素
+ erase(pos) 删除pos位置处的数据
+ erase(beg,end) 删除(beg,end)区间的数据
+ front() 返回第一个元素
+ insert(pos,elem) 在pos位置处插入一个元素
+ pop_back() 删除最后一个元素
+ push_back(elem) 在容器末尾插入一个元素
+ resize(num) 重新设置容器的大小
+ begin()、end() 返回容器首尾元素的迭代器

```c++
//例子：向量容器vector
#include <iostream>
#include <vector>
#include <algorithm> //封装好的算法文件
using namespace std;

int main()
{
  vector<double> vecDouble = {98.5, 67.9, 43.6, 32.9};
  //向数组中插入数据
  vecDouble.push_back(53.8);//在数组的尾部插入一个数字

  cout << "插入数据后：" << endl;
  //遍历1
  for(int i = 0;i < vecDouble.size(); i++)
  {
    cout << vecDouble[i] << "\t";
  }
  //集合的通用遍历方法，使用迭代器iterator
  cout << endl;
  vector<double>::iterator it; //得到迭代器对象,实际上是一个指针对象！
  // it.begin1
  for(it = vecDouble.begin(); it != vecDouble.end(); ++it)//效率的问题
  {
    cout << *it << "\t"; //必须要加星号*
  }

  //排序
  cout << endl;
  sort(vecDouble.begin(),vecDouble.end());
  for(it = vecDouble.begin(); it != vecDouble.end(); ++it)//效率的问题
  {
    cout << *it << "\t"; //必须要加星号*
  }
  return 0;
}
```

## 指针pointer
指针：指针是一个值为内存地址的变量(或数据对象)，内存地址一般使用16进制表示  

**指针的作用**：

**基本用法**
数据类型 *指针变量名

注意：
+ int* p的写法偏向于地址，即p就是一个地址变量，表示一个十六进制地址  
+ int *p的写法偏向于值，*p就是一个整形变量，能够表示一个整形值  
+ 声明中的*号和使用中的*号的含义完全不同

空指针不指向任何对象，在视图使用一个指针之前可以首先检查是否为空

void *指针，，一种特殊类型，可以存放任意对象的地址
void类型指针一般用来：用来和别的指针比较，作为函数的输入和输出：赋值给另一个void *指针


```c++
//例子：指针
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{
  //变量
  int year = 2016;
  //一个整形的指针，取year变量的地址复制给ptr_year
  int* ptr_year = &year; //指针在名字前多加一个星号，&变量可以获得变量的地址

  cout << "*ptr_year = " << *ptr_year << endl; //*ptr_year=2016
  cout << "ptr_year = " << ptr_year << endl; //ptr_year=0x61ff18
  cout << "year = " << year << endl; //year=2016
  cout << "&year = " << &year << endl; //&year=0x61ff18

  *ptr_year=2019;
  //num=2019;这两句话是等价的哦；

  //思考题
  char ch = 'a';
  char * ptr_ch = &ch;
  cout << "*ptr_ch = " << *ptr_ch << endl; //*ptr_ch=a
  cout << "ptr_ch = " << ptr_ch << endl;   //ptr_ch=a?
  cout << "(void *)ptr_ch = " << (void *)ptr_ch << endl;   //0x61ff13
            //任意类型
  //因为在c++中，char型指针被当成了字符串，所以要用(void *)强行转换成任意类型的指针

  int *ptr1 = nullptr;//等价于int *ptr1=0;
  int *ptr2 = 0; //直接将ptr初始化为字面常量
  //需要包括cstdlib
  int *ptr = NULL; //等价于int  ptr = 0;

//  cout << "*ptr2 = " << *ptr2 << endl; //*ptr_ch=a
  cout << "ptr = " << ptr << endl;   //ptr=0
  cout << "ptr1 = " << ptr1 << endl;   //ptr1=0
  cout << "ptr2 = " << ptr2 << endl;   //ptr2=0

  return 0;
}
```
**引用：**
+ 给对象起了另外一个名字（引用即别名）
+ 引用只能绑定在对象上，不能与字面值或某个表达式的计算结果绑定在一起
```c++
                    int &refValue = 10;//错误
```
+ 引用必须初始化，所以使用引用之前不需要测试其有效性，因此使用引用可能会比使用指针效率高
+ 指向常量的引用是非法的
```c++
                    const double& ref=100;//错误
```

引用和指针的关系：
+ 引用对指针进行了简单封装，底层仍然是指针
+ 获取引用地址时，编译器会进行内部转换

指针与数组
+ 数组是一片连续的变量空间
