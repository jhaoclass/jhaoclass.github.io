# 第一章 -先行知识

## 1、Typora介绍

## 2、计算机组成

硬件：CPU、GPU、内存、外存

软件：系统软件、用户软件

## 3、windows命令

1. cmd的使用
   - 软件可以打开
2. 文件后缀打开
   - 各种快捷键

## 4、二进制的存储

1、内存像Excel表格一样

- 内存地址

2、存储单元

- 1bit = 1个二进制位-一位
- 1Byte = 8bit
- 1KB = 1024B
- 1MB = 1024KB
- 1GB = 1024MB
- 1TB = 1024GB

3、二进制的加减计算

- n进制就是逢n进1
- 最高位是一个符号位
- 原码、反码、补码
- 自带的计算器可以进行进制转换
- 短除法

4、逻辑运算

- 与(&)：有0则0
- 或(||)：有1则1
- 非(!)：转换
- 异或(^)：相同为0.不同为1

## 5、网络

传输的是电信号或者光信号

家里网络是200M，其实是200MHz，

但是运营商的200M每秒可以发送200M个比特位

但是下载的速度是MByte

就是家庭宽带的理论下载速度是200M/8得到的就是理论下载速度

## 6、Java是什么？

### （1）Java是一种计算机编程语言

- 编程的目的就是写程序或者软件，程序就是我们对计算机发出的指令集
- Java就是用来写程序的，语言就是用来交流的
- 为了能让计算机看懂，Java会有一系列的规定，这就是Java的语法（组成语言最基本的东西）

### （2）Java是一种软件开发、运行、部署的平台

- 简单来说，我们可以使用Java语言开发出应用程序，部署并且安装在有Java环境的计算机上。
- Java环境——类似安卓虚拟机

## 7、Java能干什么

### （1）桌面级应用

- word、excel

### （2）企业级应用

- 大规模的应用，一般使用人数较多，数据量较大，对系统的稳定性、安全性、可扩展性和可装配性都有比较高的要求。
- 这是Java应用最广泛的领域，几乎就是一枝独秀，领域涉及：办公自动化OA、客户关系管理CEM、人力资源HR、记账、报表

### （3）嵌入式设备

- 手机上的软件

### （4）大数据领域产品

- 很多大数据的软件都是使用Java编写的，所以Java也是大数据的基础

## 8、Java历史

- 现在发展到Java16了，但是使用最多的是Java8
- Java虚拟机不是跨平台的，每种系统有自己的虚拟机

9、JDK、JRE、JVM

- JDK ： `Java开发者工具包`，JDK = JRE + Java开发者工具[java、javac、javadoc、javap]，JDK是提供给java开发人员使用的，其中包含了java 的开发工具 ，也包括了JRE，所以安装了JDK就不用安装JRE了。
- JRE ：` Java运行时环境`,JRE = JVM + Java的核心库[类]，如果需要运行一个已经开发好的Java程序，计算机中只需要安装JRE即可。
- JVM ： `Java虚拟机`，



# 第二章-数据类型

## 1、HelloWorld

### （1）怎么使用cmd编译

javac.exe就是编译器能把编译器中的英文转化成二进制指令

.class就是二进制文件

```java
"C:\Program Files\Java\jdk1.8.0_221\bin\javac" HelloWorld.java
```

```java
"C:\Program Files\Java\jdk1.8.0_221\bin\java" HelloWorld
```

注意输入的是英文的字母以及符号

- `配置环境变量`之后就不需要引号中的大部分，只需要`javac HelloWorld.java`,`java HelloWorld`
- `path`，是告诉系统，当要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在`当前目录`下面寻找此程序外，还应到哪些目录下去寻找。

### （2）`环境变量配置`

- path：将bin目录添加进path中，如果运行的目录没有javac，就去path中挨个寻找。
- 但是一般不是上面的办法，是添加一个`JAVA_HOME`变量，值是Java的`jdk`目录，然后在path中添加`%JAVA_HOME%\bin`

## 2、数据类型

### （1）`四类八种`

整型、浮点型、字符型、布尔型

| 数据类型 | 占用内存 | 取值范围                                                     |
| -------- | -------- | ------------------------------------------------------------ |
| byte     | 1个字节  | -2^7 ~ 2^7-1                                                 |
| short    | 2个字节  | -2^15 ~ 2^15-1                                               |
| int      | 4个字节  | -2^31 ~ 2^31-1                                               |
| long     | 8个字节  | -2^63 ~ 2^63-1                                               |
| float    | 4个字节  | （正数）1.4E-45  - 3.4028235E38  （整体） -3.4028235E38 ~ 3.4028235E38 |
| double   | 8个字节  | 1.7976931348623157E308 ~ 4.9E-324                            |
| char     | 2个字节  | 65536（看字符编码）                                          |
| boolean  | 1个字节  | 两个值 true和false                                           |

- 整数的负数的取值范围是用高位溢出和补码计算出来的

- 浮点数是用的IEEE754标准 `n = (-1)^s×M×2^E`

  - (-1)^s表示符号位，当s=0，V为正数；当s=1，V为负数。

  - M表示有效数字，大于等于1，小于2，但整数部分的1可以省略，也叫尾数。

  - 2^E表示指数位。

  - E全为0，这时指数是1-127，E全为1，表示的是一个无穷大或者无穷小

  - n进制浮点数转化成n进制定点数，乘n取整

  - 符号位、阶码、尾数

  - ```java
    System.out.println(Integer.toBinaryString(Float.floatToIntBits(-58.2F)));
    1 10000100 11010001100110011001101
    -1 * 1.11010001100110011001101 * 2^(132-127) = -1.11010001100110011001101 * 2^5
    ```

- 字符型char：其实就是规定，规定了几个bit是一个字符，然后进行对应的转换，ASCⅡ码表

  - ![image-20220622160025105](%E5%9B%BE%E7%89%87/image-20220622160025105.png)
  - Unicode(统一码、万国码)
  - GB2312(简体中文编码)，GBK(简体中文和繁体中文)
  - UTF-8(万国码的优化版)——可变长

  

## 3、定义变量

### （1）数据类型、*定义*

`long l = 17L;`定义一个long型的需要在值的后面加L；

`float f = 0.1F;`需要在数字后面添加F，系统默认浮点数是double；

`char = 'a';`只能是一个字母；

编辑器的`编码`需要跟黑窗口的一样；

### （2）标识符

1. 变量名中不能有空格(会显示不是一个变量，提示添加分号)；
2. 避免使用关键字，class、static、public；
3. 避免使用汉字，不要使用英文和拼音混着写，eg:zuiDaAge；
4. 整体是`驼峰式`命名，`首字母小写`,lowerCamelCase；
5. $和_可以到处使用；
6. 数字不能开头；
7. `标识符会转化成一个直接引用(保存值的地址)，JVM会在合适的时候把直接引用(符号引用)转化成一个具体的地址`；

## 4、数据运算

### （1）算术运算

```java
+、-、*、/、%、++、--
byte a = 127;
byte b = 127;
byte c = a + b;//报错
```

`报错原因`：比int取值范围小的数据类型计算结果都是int。

`++、--`：看一个语句中有几步，如果是一步就是没有i = i+1;如果有多步就要看位置

### （2）逻辑运算

```java
&(与)、&&(短路与)、|(或)、||(短路或)、!(非)、>=、<=、==(等于)、^(异或)
```

`区别`：短路与比与、短路或比或更加智能，如果运算符前面值的就可以得到结果，就不用判断运算符后面的值了。

|  与&   |  或\|  | 非!  |      异或^       |
| :----: | :----: | :--: | :--------------: |
| 有0则0 | 有1则1 | 取反 | 相同为0，不同为1 |

短路与(&&)：运算符前面的值为0，就直接跳过后面的值，得到结果为'假'。

与(&)：还可以进行按位与。

`单目、双目运算符`：单目运算符可以进行按位运算。

`异或加密`：原文与密文是异或得到的，`最简单的加密算法`。

### （3）赋值运算符

```java
+=、-=、*=、/=、=
```

### （4）三目运算符

```java
条件 ? 语句1 :	语句2;
```

## 5、数据类型转换

任何有精度缺失（有可能让两个数变成完全不一样的两个数）的转型都需要强转，jvm不给你负责。

取值范围大的转取值范围小的自动转，反之需要强转。



# 第三章-三种语句

## 1、顺序结构

程序就是从上到下、从左到右的执行。

## 2、分支语句

### （1）单分支

```java
import java.util.Scanner;
public class Alcohol {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int alcohol = scanner.nextInt();
        if(alcohol > 10){
            System.out.println("喝酒了，带走！");
        }
    }
}

```

### （2）双分支

```java
import java.util.Scanner;
public class Alcohol {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int alcohol = scanner.nextInt();
        if(alcohol > 10){
            System.out.println("喝酒了，带走！");
        } else {
        System.out.println("放行");
        }
    }
}

```

### （3）多分支

```java
import java.util.Scanner;
public class Alcohol {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int alcohol = scanner.nextInt();
        if(alcohol > 20 && alcohol <= 80){
            System.out.println("酒驾，带走！");
        } else if(alcohol > 80) {
        System.out.println("醉驾，判刑！");
        } else {
            System.out.println("放行");
        }
    }
}

```

### （4）嵌套分支

动物园的门票分淡季旺季，淡季20元，旺季30元，其中（1，代表淡季，2，代表旺季）

- 儿童（0~7）免费
- 学生（8~22）岁半价
- 成人（23~60）不打折
- 老人（>60岁）打三折

```java
import java.util.Scanner;
public class Zoo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("请输入现在的季节:");
        int season = scanner.nextInt();
        double value=0.0;
        System.out.print("请输入买票人的年龄:");
        if(season == 1){
            value = 20;
        } else if(season == 2){
            value = 30;
        }
        int age = scanner.nextInt();
        if(age >= 0 && age <= 7){
            value = 0;
        } else if(age >= 8 && age < 22){
            value *= 0.5;
        } else if(age >= 22 && age < 60){
            ;
        } else if(age >= 60){
            value *= 0.3;
        }
        System.out.println(value);
    }
}

```

### （5）switch语句

- 周一：和亦菲约会
- 周二：和志玲约会
- 周三：和诗诗约会
- 周四：和井空约会
- 周五：和热巴约会
- 其他时间：参加各种party

```java
import java.util.Scanner;
public class Meet {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int day = scanner.nextInt();

        switch (day){
            case 1 : System.out.println("和亦菲约会"); break;
            case 2 : System.out.println("和志玲约会"); break;
            case 3 : System.out.println("和诗诗约会"); break;
            case 4 : System.out.println("和井空约会"); break;
            case 5 : System.out.println("和热巴约会"); break;
            default : System.out.println("参加各种party");break;
        }
    }
}

```

**`注`**：break不能忘记



<img src="../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC%E5%9B%9B%E5%A4%A9-%E6%B5%81%E7%A8%8B%E6%8E%A7%E5%88%B6%E8%AF%AD%E5%8F%A5/image-20210727162939043.png" alt="image-20210727162939043" style="zoom: 50%;" />

## 3、循环语句

### （1）for语句

```java
public class ShuiXianHuaShu {
    public static void main(String[] args) {
        int a, b, c;
        int i;
        for(i = 100; i <= 999; i++){
            a = i/100;
            b = i%100/10;
            c = i%10;
            if(a*a*a+b*b*b+c*c*c == i){
                System.out.println(i+"是水仙花数");
            }
        }
    }
}

```

### （2）嵌套for循环

```java
public class JiSuanQi {
    public static void main(String[] args) {
        for (int i = 1; i < 10; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(i+"*"+j+"="+(i*j)+" ");
            }
            System.out.println();
        }
    }
}
//每一行就是乘到列数等于行数
/*
1*1=1 
2*1=2 2*2=4 
3*1=3 3*2=6 3*3=9 
4*1=4 4*2=8 4*3=12 4*4=16 
5*1=5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1=6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1=7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1=8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1=9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
*/

```

```java
//三角形
public class SanJiao {
    public static void main(String[] args) {
        for (int i = 1; i < 6; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}

```

> 给循环打标签——退出指定的循环

```java
public class SanJiao {
    public static void main(String[] args) {
        flag: for (int i = 0; i < 6; i++) {
            for (int j = 0; j < 5; j++) {
                System.out.print("*");
                if(i == 2 && j == 1)
                    break flag;
            }
            System.out.println();
        }
    }
}

```

### （3）while和do...while循环

```JAVA
// 定义 条件变量
int i = 0;
// 进入的条件
while( i < 5){
    ......
    // 变量改变,变量的改变是为了满足退出条件
    i++;
}

int i = 0;
do{
    ......
    // 变量改变,变量的改变是为了满足退出条件
    i++; 
}while(i < 7) {
    ......
    
}  

```



```java
import java.util.Scanner;
public class Teat1 {
    public static void main(String[] args) {
        int i;
        Scanner scanner = new Scanner(System.in);
        while(true){
            System.out.println("请输入一个数字");
            i = scanner.nextInt();
            if(i > 10){
                System.out.println("楠哥牛逼");
            }
        }
    }
}

```

> 区别

- do while无论如何都要先执行一下，然后才去判断
- while  满足条件才能进入

## 4、猜数字--看编程思想

猜数字小游戏，先随机输入一个数字，之后让另一个人输入，如果大了就告诉他大了，小了就告诉他小了，直到一样：

`对比两个程序的不同`

```java
import java.util.Scanner;
public class GuessNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("请输入一个数字：");
        int value = scanner.nextInt();
        System.out.print("请输入您猜的数字：");
        int num = scanner.nextInt();
        while(true){
            if(num > value){
                System.out.println("大了！");
                System.out.print("请重新猜数字：");
                num = scanner.nextInt();
            } else if(num < value){
                System.out.println("小了！");
                System.out.print("请重新猜数字：");
                num = scanner.nextInt();
            } else if(num == value){
                System.out.println("恭喜您猜对了");
                break;
            }
        }
    }
}

```

```java
import java.util.Scanner;
public class GuessNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("请输入一个数字：");
        int value = scanner.nextInt();

        int num;//定义用户输入的数字
        while(true){
            System.out.print("请输入您猜的数字：");//这两句原来在每次的判断之后都可以写，但是也可以提出来，
            num = scanner.nextInt();//外面定义，里面初始化
            if(num > value){
                System.out.println("大了！");
            } else if(num < value){
                System.out.println("小了！");
            } else if(num == value){
                System.out.println("恭喜您猜对了");
                break;
            }
        }
    }
}

```

# 第四章-数组和算法

## 一、数组的定义

### 1、基本概念

- 数组是引用数据类型；
- 数组名在栈中，数组内容在堆中，分配在一块连续的内存中；
- 计算机有2^位数次方根地址线；

```java
定义：
int[] nums;
初始化：//在堆内存中分配空间
nums = new int[3];
赋值：
nums[0] = 1;   
nums[1] = 4;
nums[2] = 3;

// 直接定义初始化并赋值
int[] nums = {1,2,3};

// 这样写也行
int nums[] = new int[5];
int nums[] = new int[]{1,2,4,5};

// 数组有一个属性，可以获得数组的长度
nums.length 

类型[] 名字 = new 类型[长度];

```

**问题**：

1. 数组不初始化有值吗？

   数组不初始化有初始值；

2. 数组不初始化能赋值吗？

   不初始化不能赋值，因为不初始化就没有在堆内存中分配空间；

3. 数组是否能越界？

   数组不能越界，会提示数组下标越界；

### 2、数组的性质

1. 数组一旦建立，长度不能改表；
2. 每个位置只能保存一个值，如果多次赋值会覆盖；
3. 数组初始化之后会有默认值：int 0、short 0、byte 0、long 0、float 0.0、double 0.0、char \u0000、boolean false、String null；
4. 数组下标从0开始，下标必须在指定范围内使用，否则报：下标越界异常；
5. 有个长度属性，第一个下标是0，最后一个是length-1；
6. 数组中可以是基本数据类型，也可以是引用数据类型；

### 3、数据结构

数组是一种`最基本的`数据结构，是`表`的一种，是一种二维的线性表，我们以后还会接触链表，hash表等。

百度百科是这样解释线性表的：

- 线性表是最基本、最简单、也是最常用的一种数据结构。线性表*（linear list）*是数据结构的一种，一个线性表是n个具有相同特性的数据元素的有限序列。
- 线性表中数据元素之间的关系是一对一的关系，即除了第一个和最后一个数据元素之外，其它数据元素都是首尾相接的）。

## 二、玩转数组

### 1、数组的遍历

```java
public class Ergodic {
    public static void main(String[] args) {
        int[] nums = {12, 11, 10, 5, 1};
        int i;
		//使用for进行遍历
        for (i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
        
        System.out.println();
        //使用while进行循环
        i = 0;
        while(i < nums.length){
            System.out.println(nums[i]);
            i++;
        }
    }
}


```

### 2、查找数组中存在的某一个值--使用下标

```java
import java.util.Scanner;

public class FindOne {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4, 5, 99};
        //目标值
        Scanner scanner = new Scanner(System.in);
        int target = scanner.nextInt();

        //resule保存下标，利用了数组的下标没有负数
        int result = -1;

        //遍历寻找
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target){
                result = i;
                break;
            }
        }

        //判断输出
        if (result < 0 || result >= nums.length){//进行严格判断，防止以后项目中中途有人改变数值
            System.out.println("找到了这个人了，身份证号是是："+nums[result]);
        } else if(result == -1){
            System.out.println("没找到这个人，这个人还没登记");
        }

    }
}

```

### 3、打擂台的形式找最大值--使用下标

```java
public class ArrayMax {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 77, 8, 4, 5};

        //定义一个擂台,使用的是最大值的下标
        int max = 0;

        //遍历比较
        for (int i = 1; i < nums.length; i++) {
            if(nums[i] > nums[max])
                max = i;
        }

        //输出最大值
        System.out.println(nums[max]);
    }
}


```

### 4、元素的位移--交换两个数字

```java
public class ArrayChange {
    public static void main(String[] args) {
        int[] nums = {1, 2, 4, 3};
        //中间变量
        int t = 0;
        //交换两个数字
        t = nums[2];
        nums[2] = nums[3];
        nums[3] = t;

        //遍历输出
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
    }
}

```

### 5、数组的扩容

1. 定义一个大数组
2. 拷贝有效数据
3. 改变引用

```java
public class Dilatation {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        int[] temp;//定义长数组
        temp = new int[nums.length*2];//临时数组分配内存
        //扩容过程
        for (int i = 0; i < nums.length; i++) {
            temp[i] = nums[i];//有效数据保存
        }
        nums = temp;//引用转变
        
        nums[3] = 4;
        nums[4] = 5;
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
    }
}

```

### 6、数组的反转

#### 方法一

定义一个等长的临时数组，进行反转

```java
public class FanZhuan {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4, 5};
        int[] temp = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            temp[i] = nums[nums.length-1-i];
        }
        nums = temp;
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
    }
}

```

#### 方法二

单个数组进行元素交换

```java
public class FanZhuan {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4, 5, 6};
        int t;
        
        //交换
        for (int i = 0; i < nums.length/2; i++) {
            t = nums[i];
            nums[i] = nums[nums.length-1-i];
            nums[nums.length-1-i] = t;
        }
        
        //遍历
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
    }
}


```

### 7、元动力人事系统

1. 可以不断的选择功能，有控制台；
2. 可以输入工号，可以保存在数组中；
3. 可以查找具体的工号；

思路：可以不断的进行操作，是在循环中进行操作，进行功能选择，需要scanner进行输入，1是输入工号，然后数组扩容，改变引用，2是进行查找工号，进行遍历查找 

```java
import java.util.Scanner;
public class TaskYuanDongLi {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] nums = {001, 002};
        int choice;//选择功能
        System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
        choice = scanner.nextInt();//控制台输入
        int jobNumber;
        while(choice != 0){
            //添加工号
            if(choice == 1){
                System.out.print("请输入需要添加的工号：");
                jobNumber = scanner.nextInt();
                int[] temp = new int[nums.length+1];
                for (int i = 0; i < nums.length; i++) {//拷贝数据
                    temp[i] = nums[i];
                }
                temp[nums.length] = jobNumber;//添加工号
                nums = temp;//改变引用
                System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                choice = scanner.nextInt();//控制台输入
            } else if(choice == 2){
                System.out.print("请输入需要查找的工号：");
                jobNumber = scanner.nextInt();
                for (int i = 0; i < nums.length; i++) {
                    if(nums[i] == jobNumber){
                        System.out.println("找到这个人的工号，是元动力工作人员。");
                    }
                }
                System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                choice = scanner.nextInt();//控制台输入
            } else if(choice == 0){
                System.out.println("退出成功！");
                break;
            } else if(choice == 3){
                for (int i = 0; i < nums.length; i++) {
                    System.out.println(nums[i]);
                }
                System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                choice = scanner.nextInt();//控制台输入
            } else {
                System.out.println("选择错误，请重新输入");
                System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                choice = scanner.nextInt();//控制台输入
            }
        }
    }
}

```

使用switch替换if

```java
import java.util.Scanner;
public class TeskYuanDongLiTwo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] nums = new int[1];
        int jobNumber;
        int choice;
        System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
        choice = scanner.nextInt();
        int index = 0;
        while(true){
            switch (choice){
                case 0 :
                    break;
                case 1 :
                    System.out.print("请输入添加的工号：");
                    jobNumber = scanner.nextInt();
                    int[] temp = new int[nums.length+1];
                    nums[index++] =jobNumber;
                    for (int i = 0; i < nums.length; i++) {
                        temp[i] = nums[i];
                    }
                    nums = temp;
                    System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                    choice = scanner.nextInt();;
                    continue;
                case 2 :
                    System.out.print("请输入需要查找的工号：");
                    jobNumber = scanner.nextInt();
                    int t = -1;
                    for (int i = 0; i < nums.length; i++) {
                        if(jobNumber == nums[i]){
                            t = i;
                        }
                        if (t >= 0 && t < nums.length){
                            System.out.println("找到该工号了");
                        }
                        if(t < 0 || t == nums.length){
                            System.out.println("没找到该工号");
                        }
                    }
                    System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                    choice = scanner.nextInt();;
                    continue;
                case 3 :
                    for (int i = 0; i < nums.length; i++) {
                        System.out.println(nums[i]);
                    }
                    System.out.print("请进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                    choice = scanner.nextInt();;
                    continue;
                default:
                    System.out.println("输入错误，请重新进行功能选择，0是退出，1是添加，2是查找，3是遍历：");
                    choice = scanner.nextInt();;
                    continue;
            }
        }
    }
}

```

## 三、debug

可以帮助我们检查错误，步入步出，看懂别人的程序，看程序中变量值的变化，看懂别人的程序。	

# 第五章-算法

## 一、初识算法

数据结构是把数据在内存或磁盘存放时的规矩。是一个图书馆的书架，格子都给你规定好了，我们可以按照预设的方式去摆放图书。

算法是具体的动作，是怎么去摆放，怎么快速的找到我要的图书。

​		注意，我们的课程主线是怎么敲代码，在学习JavaSE的阶段如果太痴迷于算法，你就学不完了。但是如果你大一大二时间多，那没问题。我会在后期的附加课中，讲解每一种排序方法，这里我们只选择讲解最简单的。

## 二、基础算法

1. 简单排序：选择排序、插入排序、冒泡排序
2. 高级排序：希尔排序、快速排序、归并排序
3. 特定场景使用：堆排序、桶排序、基数排序

### （1）冒泡排序

- 每一轮都是两两排序，大的靠后站，经过一轮下来，最大的值会到最后。

1. 比较多少轮
2. 每轮比较到哪里

```java
public class MaoPao {
    public static void main(String[] args) {
        int[] nums = {4, 2, 3, 1, 5, 6, 7, 0, 9, 8};
        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < nums.length-i; j++) {
                int t;
                if(nums[j] > nums[j+1]){
                    t = nums[j];
                    nums[j] = nums[j+1];
                    nums[j+1] = t;
                }
            }
        }
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
    }
}

```

### （2）查找算法-二分查找(折半查找)

一般情况下，在一般的系统中，查找的次数远远大于插入的次数，所以程序对查找的要求更高一些。

自己写的

```java
import java.util.Scanner;

public class BinarySearch {
    public static void main(String[] args) {
        int[] nums = {1, 42, 5, 3, 4, 7, 55, 8};
        //排序
        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < nums.length-i; j++) {
                if(nums[j] > nums[j+1]){
                    int temp;
                    temp = nums[j];
                    nums[j] = nums[j+1];
                    nums[j+1] = temp;
                }
            }
        }
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
        //查找
        Scanner scanner = new Scanner(System.in);
        //需要查找的数字
        System.out.print("请输入需要查找的数字：");
        int target = scanner.nextInt();
        //定义边界+中间
        int left = 0;//左边界
        int right = nums.length-1;//右边界
        int mid = (right-left)/2;//中心
        int flag = 0;
        while(left <= right){//使用左右边界不重合
            if(target < nums[left] || target > nums[right]){//目标值在有序数组之外
                System.out.println("查询的值不在数组中！");
                break;
            } else if(target == nums[left] || target == nums[mid] || target == nums[right]){
                System.out.println("找到该数字了");
                flag = 1;
                break;
            } else if (target > nums[left] && target < nums[mid]){//在左一边
                left = mid+1;
                mid = (right-left)/2;
                continue;
            } else if(target > nums[mid] && target < nums[right]){//右一边
                right = mid-1;
                mid = (left+right/2);
                continue;
            } else if(flag == 0){
                System.out.println("未找到该数字");
                break;
            }
        }

    }
}

```

方法2

```java
Scanner scanner = new Scanner(System.in);
//需要查找的数字
System.out.print("请输入需要查找的数字：");
int target = scanner.nextInt();
//定义边界+中间
int left = 0;//左边界
int right = nums.length - 1;//右边界
int mid = (right + left) / 2;//中心
int res = -1;//下标
while (left <= right) {
    if (target < nums[left] || target > nums[right]) {
        System.out.println("查询的值不在数组中");
        break;
    }
    if (target == nums[mid]) {
        System.out.println("找到该数字了");
        res = mid;
        break;
    } else if (target < nums[mid]) {
        mid = mid - 1;
    } else if (target > nums[mid]) {
        mid = mid + 1;
    }
}


System.out.println("在数组中的下标是：" + res);

```

## 三、算法性能

### （1）时间复杂度

通常我们考虑一个算法的指标是看其在时间和空间两个维度的表现决定的。

- 时间维度：是指执行当前算法所消耗的时间，我们通常用「时间复杂度」来描述。
- 空间维度：是指执行当前算法需要占用多少内存空间，我们通常用「空间复杂度」来描述。
- 随着操作数据的增多，完成这个程序所需要的时间
- 随着操作数据的增多，完成这个程序需要分配的空间

**a、线性阶**

我们先来看个我们之前的例子：

```text
int targetIndex = -1;
for (int i = 0; i < salary.length; i++) {
    if(salary[i] == 9){
        targetIndex = i;
    }
    break;
}

```

通过「 大O符号表示法 」，这段代码的时间复杂度为：O(n) ，为什么呢?

对于我们这种顺序检索，随着数组的大小的变化，查询需要遍历的次数也会线性增长，n就好比要查找的次数。

**b、常数阶**

那如果有这么一种算法，无论数组多长，查询只需要一次就能出结果，这样的时间复杂度就是O(1)，后边我们会学习hash。

**c、指数阶**

思考，我们的冒泡排序呢？

随着数组长度的变化，我们遍历的次数是指数级增长的，那它的时间复杂度就是O(n^2)。



**d、对数阶**

思考、我们的二分查找法呢

试想：

- 一个有序数组长度为8 最多需要3次即可，应为也只能折3次；
- 一个有序数组长度为16 最多需要4次即可，应为也只能折4次；
- 一个有序数组长度为32 最多需要5次即可，应为也只能折5次。

**e、高级排序**

高级排序会在后续的附加课一一讲解，咱们就不再细说了。

O(logN*n)

### （2）空间复杂度

和时间复杂度类似，空间复杂度就是在我的算法下，数据的长度越长，你额外需要多少空间。

比较常用的有：O(1)、O(n)、O(n²)，我们下面来看看：

**a、空间复杂度 O(1)**

如果算法执行所需要的临时空间不随着某个变量n的大小而变化，即此算法空间复杂度为一个常量，可表示为 O(1)
比如咱们刚刚学习的冒泡排序，二分查找，无论数组多长，我们依然不需要更多的额外空间。



**b、空间复杂度 O(n)**

思考我们的数组反转：

> 思路一：创建一个等长的数组，反向放入，最后改变引用即可

这种方法，你的数组越长，总是需要一个等长的数据作为额外空间，这种增长是线性的，所以它的空间复杂度是O(n);

它的时间复杂度呢？  O(n)

#### 

> 思路二：利用首尾两两交换的方法

这种方法，你并不需要去创建额外的空间，所以它的空间复杂度是O(1);

它的时间复杂度呢？  O(n/2)



很明显，第二种方法在时间复杂度和空间复杂度上都要更加优秀。

- 算法是有优劣的。有的人写的是真牛逼，有的人写的是真辣鸡。
- 一段代码的性能和代码的长短没有毛线关系，不是越长的越好，也不是越短的越好。

## 四、归并的思想

int[] array1 = {1,3,5,8,12,35,54,456,2545};

int[] array2 = {2,4,7,10,40,60};

### 思路一：

创建一个大的数组，长度为两个数组之和，然后冒泡排序。

### 思路二：

归并思路如下：

1、同时遍历两个数组，遍历的当前值进行比较，小的放入新数组。

2、放进去之后，数据继续遍历，指针后移。

3、经过多次遍历

- 如果某一个数组指到最后一位时，另一个数组应该直接拷贝，继续执行会提示下标越界，所以 需要continue；
- 数组下标的关系
- 清楚为什么使用多次嵌套分支——`使用continue可以巧妙的解决一直报错下标越界`

```java
public class TwoArray {
    public static void main(String[] args) {
        int[] array1 = {1, 4, 6, 8, 12};
        int[] array2 = {3, 5, 7, 36, 46};
        //使用下标代替指针
        int i = 0;
        int j = 0;

        //创建一个新数组
        int[] array = new int[array1.length + array2.length];
        int t = 0;

        //开始同时遍历
        while (i < array1.length || j < array2.length) {
            if (i == array1.length) {
                array[t++] = array2[j++];
            } else if (j == array2.length) {
                array[t++] = array2[i++];
            } else if (array1[i] < array2[j]) {
                array[t++] = array1[i++];
            } else {
                array[t++] = array2[j++];
            }
        }
        System.out.println(t);

        for (int k = 0; k < array.length; k++) {
            System.out.println(array[k]);
        }
    }
}

```

```java
/*如何解决上面的嵌套分支*/
public class TwoArray {
    public static void main(String[] args) {
        int[] array1 = {1, 4, 6, 8, 12};
        int[] array2 = {3, 5, 7, 36, 46};
        //使用下标代替指针
        int i = 0;
        int j = 0;

        //创建一个新数组
        int[] array = new int[array1.length+array2.length];
        int t = 0;

        //开始同时遍历
        while(i < array1.length || j < array2.length){
            if (i == array1.length){
                array[t++] = array2[j++];
                continue;
            }
            if (j == array2.length){
                array[t++] = array2[i++];
                continue;
            }
            if(array1[i] < array2[j]){
                array[t++] = array1[i];
                i++;
            } else {
                array[t++] = array2[j];
                j++;
            }
        }
        System.out.println(t);

        for (int k = 0; k < array.length; k++) {
            System.out.println(array[k]);
        }
    }
}

```

## 五、二维数组

```java
 int nums[][]=new int[2][3];

```

```java
public class YangHui {
    public static void main(String[] args) {
        int[][] nums = new int[10][];
        for (int i = 0; i < nums.length; i++) {
            nums[i] = new int[i+1];
        }
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums[i].length; j++) {
                if(j == 0 || i == j)
                    nums[i][j] = 1;
                else
                    nums[i][j] = nums[i-1][j-1]+nums[i-1][j];
            }
        }


        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums[i].length; j++) {
                    System.out.print(nums[i][j] + "   ");
            }
            System.out.println();
        }
    }
}

```

# 第六章-面向对象-2022/6/30

## 一、面向对象概述

### 1、面向对象介绍

Java是一门面向对象的语言，在Java中一切皆对象。

#### （1）面向对象和面向过程

- 面向过程——步骤化
  - 面向过程就是分析出实现需求所需要的步骤，通过函数(方法)一步一步实现这些步骤，接着依次调用即可。
- 面向对象——行为化(概念相对抽象)
  - 面向对象是把整个需求按照特点、功能划分，将这些存在共性的部分**封装成类**(类实例化之后才是对象)，让对象解决相应的问题。

#### （2）用例子思考

其实我们之前写的代码都是面向过程的，而事实上，我们的大脑处理问题本身就是更加偏向面向对象的。

> 举一个例子：

你想送你女朋友一个包，

- 面向对象的思想是，找个卖包包的店，买一个包包。其中不管是商店，还是包都是现实生活中存在的事物，代码里我们称之为对象。
- 面向过程的思想是：找到原材料，自己切割，自己缝制，每一个工序都自己干，这就是过程。

感觉面向对象忽略了过程一样。



其实，越是高级的语言会越向着人的思考靠近。

- 面向对象是更高级的抽象，是对现实世界的映射。
- 思考一下，我们接触过的 String、Scanner就是很好的例子。你看着很简单的字符串，它本身就是个对象，不需要我们自己去完成一个字符一个字符的拼接，Scanner更是牛逼，我们更加不知道它具体是怎么做到让我们从控制台输入的，事实上我们知道它能做什么就足够了。
- 这就是别人给我们创造的对象，事实上我们也能给自己创造对象，我们也能给别人创造对象。
- 就像现实中一样，你想吃水果，就去水果摊买；你想按脚，就去足疗店，你想玩，可以去迪斯尼。
- 当然你也可以开个4s店卖汽车。
- 没人会关心水果是怎么种的，从哪里来的，按脚的技师是怎么招聘的，迪斯尼是怎么建的，4s店的车是怎么造的。我们关心的只是水果、技师、迪斯尼、汽车这些实实在在的对象而已。

### 2、学习自己造对象

我们准备开个4s店，我们需要车、需要门店对吧，那我们就尝试去搞一个。



- 先说说我们怎么去用代码描述一辆车：

  定义好多个变量  1、brand     2、color   3、length.........

- 问题又来了，我们怎么描述好几个车？

  [一号车的品牌，二号车的品牌，三号车的品牌...一百号汽车的品牌]

  [一号车的颜色，二号车的颜色，三号车的颜色...一百号汽车的颜色]

  .....

  

我们用了几十个数组去维护一百辆汽车的属性，这简直就是个灾难，数据简直没办法维护，每修改一辆车，必须修改每一个数组。



> 思考：我们能不能这样去搞呢？

搞一个数组，它就是汽车的数组。

[一号汽车的所有，二号汽车的所有，三号汽车的所有，...一百号汽车的所有]

这样我们一个数组就能维护所有的汽车。

同时，我们已经尝试去面向对象编程了，我们将一个汽车的多个属性尝试进行了打包，这个过程就是在`封装对象`。

**Java是一门面向对象的语言，他面向的对象也是可以单独拿出来的**

## 二、面向对象之封装

### 1、class和对象

第一步：我们要造车了，必须有个造车的说明书。

第二步：根据说明书，造一百辆车。

```java
public class Car {//封装了一个汽车类
    //品牌
    String name;
    //颜色
    String color;
    //长度
    long length;

    public static void main(String[] args) {
        Car car = new Car();
        /*
        * car在栈中
        * new出来的car在堆里面
        * 意思就是car是符号引用，指向堆内存中的car成员数组
        * */
        car.name = "BMW";
        car.color = "white";
        car.length = 1000;
  //      System.out.println(car);//输出的是内存地址  //car是一个符号引用，在JVM运行的时候会将符号引用转化为实实在在的内存地址
  //      System.out.println(car.color);

        Car benz = new Car();
        benz.name = "Benz";
        benz.color = "black";
        benz.length = 2000;

        Car[] cars = {car, benz};
        for (int i = 0; i < cars.length; i++) {
            System.out.println(cars[i].name);
        }

    }
}

```

- **Car是`类`，只有一份。**
- car1、car2、……car100是根据Car类创建出来的[实例对象]，可以有很多个。

> 内存图

![image-20210720112436796](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210720112436796.png)

- **具体解释：**
- cars数组指向堆中的一个8字节的空间，其中每4字节是一个地址，指向另外两个空间
- car1、car2都是符号引用，会在JVM运行时转化成具体的内存地址





### 2、成员变量-对象中的属性

```java
public class Car {
    // 汽车的型号
    String name;
    // 汽车的颜色
    String color;
    // 汽车的长度
    double length;
}

```

成员变量我们已经学过了，

像汽车型号、颜色、车长等属性，是Car这个类的成员，是每个实例对象都有的属性，我们称之为【成员变量】。

成员变量的赋值：

```java
car2.brand = "宝马";

```

- 只要对象被new出来，都有初始值，不需要初始化，比如上面的就是分配了一个16字节的空间，8字节放long，剩下的8字节放两个符号引用，存放地址。



### 3、成员方法-对象中的方法

- 每个对象不止有自己的属性，还有他的行为，比如车会漂移，需要加油……这些行为只有属性是不可以描述的，这些行为需要成员方法来进行实现。
- 属性是用来描述对象的，而方法是用来让对象进行一系列的操作的。

#### （1）定义成员方法

```java
public void run(String name){
    System.out.println(name + "跑起来了！");
}

```



#### （2）参数

```java
public void run(int gasoline){
        System.out.printf("您加了%d号汽油",gasoline);//printf进行一些输出格式化
        if(gasoline == 92){
            System.out.println("92号汽油跑的很快！");
        } else if(gasoline == 95){
            System.out.println("95号汽油跑的更猛！");
        } else {
            System.out.println("你加了柴油吧！");
        }
    }

```



#### （3）返回值

return：结束当前方法

```java
public boolean run(){
        // 这句代码能生成一个0~1的double的数字
        double random = Math.random();
        if(random > 0.5){
            System.out.println("车子正常启动！");
            return true;
        } else {
            System.out.println("车子坏了！");
            return false;
        }
    }

```

#### （4）方法调用

![image-20210720163640565](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210720163640565.png)

#### （5）方法递归

```java
public class DiGui {

    //斐波那契的第i项是多少
    public int feibona(int i){
        if(i == 0 || i == 1)
            return 1;
        else
            return feibona(i - 1)+feibona(i -2);
    }

    public int jc(int n){
        if(n == 1)
            return 1;
        else
            return jc(n - 1) * n;
    }
    public static void main(String[] args) {
        DiGui digui = new DiGui();
        int t = digui.feibona(10);
        System.out.println(t);
        System.out.println(digui.jc(3));

    }
}

```



#### （6）方法重载

在Java的同一个类中 ，允许有多个同名方法的存在，但要求【形参列表】不一致！这个和【返回值】无关，就带来了方法的重载。

**方法名相同，形参列表不同**——形参的数量不同、形参的数据类型不同，仅此而已，返回值类型不同也不行，

```java
public class max {
    public int max(int a, int b){
        return a > b ? a : b;
    }
    public int max(int a, int b, int c){
        int t = max(a, b);
        return t > c ? t : c;
    }

    public static void main(String[] args) {
        int a = 1;
        int b = 2;
        int c = 3;
        max m = new max();
        System.out.println(m.max(a, b, c));
    }
}

```

#### （7）可变参数

意思就是参数的数量可以改变，参数是一个数组

```java
public int plus(int[] nums){
    
}
//调用
int t = plus(new int[]{1, 2, 3})

```

```java
public int plus(int... nums){
    
}
//调用
int t = plus(1, 2, 3);

```

**一个方法的可变参数只可以有一个**——如果有多个就区分不开了，但是数组就可以

**可变参数可以跟其他变量一起使用，但是需要放到最后**——你都不知道，凭什么让JVM知道

#### （8）局部变量和作用域——*需要二刷*

- 成员变量会有默认值，就算不初始化也会有默认值。基础数据类型是0，char是空字符，boolean是false，引用类型是null；
- 局部变量没有默认值，必须初始化才能使用，不调用该成员方法是不分配空间的。



**要学会引用数据类型，所有被new出来的对象都是引用数据类型，他们的内存分布都是一个符号引用指向内存的一片空间，jvm在程序运行的时候会将符号引用转化为直接引用，就是一个地址指向具体的封装了对象的属性的值的一片内存地址**

### 4、权限修饰符

#### （1）类之间相互调用

`public`



#### （2）包

- 可以在src中new一个package，包名字叫a，然后将某个.java文件放入，代码最上方就有package a;

- 带出了`全限定名称` 的概念，包名.包名.类名

- 包名是使用当前公司的域名倒置

- ```java
  zhidao.baidu.com
  wenku.baidu.com
  image.baidu.com
      
  com.baidu.zhidao
  com.baidu.wenku
  com.baidu.image
  
  ```

  一个.是一个文件夹，可以看出域名倒置使用可以更简单的管理文件

  > 使用域名做包名的好处

  - 引入其他人写的类的时候不怕重名；
  - 一眼就能知道作者

  > 怎么导入一个包

  - 引入单个类：`com.ydlclass.entity.Car`
  - 引入包下所有类：`com.ydlclassentity.*`

  > 一个类的全限定名称

  - com.ydlclass.entity.Car

#### （3）权限修饰符

- 我们可以按照我们的要求和想法，对封装在对象中的属性和方法提供不同的权限，这就需要权限修饰符来进行修饰

| 作用域                      | 当前类 | 同package | 子孙类 | 其他package |
| --------------------------- | ------ | --------- | ------ | ----------- |
| public(公共的)              | √      | √         | √      | √           |
| protected(受保护的)         | √      | √         | √      | ×           |
| friendly( default )(友好的) | √      | √         | ×      | ×           |
| private(私有的)             | √      | ×         | ×      | ×           |

> - public是所有的都可以使用
> - private是只有自己能使用
> - friendly不用写权限修饰，在同包的类中可以相互使用
> - 权限修饰符主要使用在成员方法和成员变量
> - class只能用public使用
> - 局部变量不能使用权限修饰符



### 5、构造器-每个类都有，JVM给的

```java
//创建对象
Car car = new Car();

```

#### （1）new一个对象的时候发生了什么事情

1. Java在new一个对象的时候，会先查看对象所属的类有没有被加载到内存，如果没有的话，就会先通过这个类的全限定名称来加载这个。
2. 加载并初始化类完成后，再进行对象的创建工作。
3. 写出来的.java文件会被编译成.class文件，在构造的时候会根据classpath调用进方法区运行
4. 跨平台是JVM带来的，JVM就是一个平台

#### （2）创建的过程：

1. 在堆内存中分配对象需要的内存空间——放成员变量具体的值，方法在方法区；
2. 对所有的成员变量赋初始值；
3. 执行构造方法，
4. 把栈区内定义引用变量，然后将堆区内成员变量的地址赋给它。
5. 新的内存空间放的新的值，放进堆内存中，包裹这个值的叫做实例对象，每一个实例对象都有不同的实例属性的值，但是他们的方法是一样的。

![image-20210721161510350](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210721161510350.png)

#### （3）构造器(构造方法)-Car()

##### 1、JVM送的无参没有方法体的构造器

```java
//无参无方法体的构造器
publid Car(){
    
}

//无参构造调用
Car car = new Car();

//有参构造器
public Car(String name2, String color2, long length2){
        name = name2;
        color = color2;
        length = length2;
}

//有参构造器调用
Car bmw = new Car("bmw", "white", 1000);



```

`new做的工作就是为成员分配空间`，初始化内存空间的初始值

`Car("bmw", "white", 1000)`就是一个构造器，就是传递的三个参数

`如果自己定义了构造器，最好将系统在自动送的无参构造器定义一次，万一真的会使用普通的Car cae = new Car();`

##### 2、构造方法需要和类名保持一致，可以重载	

##### 3、在一个构造器中使用另一个构造器，我们使用this

```java
//无参构造
public Car(){
    this("benz", "black",1000);
}

```

##### 4、方法中不可以调用构造器



### 6、this关键字—指向的是new出来的空间

- 记住一点：每一个方法都会默认传入一个变量叫this，它永远指向调用它的【当前实例】

![image-20210813143046989](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210813143046989.png)

1. this可以出现在构造器、构造方法，成员方法中，每一个构造方法和成员方法都会默认传入一个默认的局部变量this，this永远指向调用它的实例对象，this是属于方法的，不是属于实例对象的
2. 首先在内存中构建了一片空间，里面放的name、color、length，其中还有一个引用，指向具体的类的字节码文件，类的字节码文件中就有方法，方法中就有this关键字，
3. 我们在调用方法的时候，比如car.run，是先通过car找到具体的实例对象，实例对象又有引用指向字节码文件中的方法，然后去调用这个方法，就是在写代码的时候，是不知道 this指向谁的，只有在调用的时候，从实例对象的符号引用找到方法，从方法中的this指向调用这个方法的实例
4. 构造的是哪个对象，指向的就是哪个实例对象
5. 一个方法想调用当前类的方法也可以使用this
6. 是一个成员变量，只在方法中可以使用

> 解：

```java
this.name = name;

```

`this指向的是new出来的空间，意思就是将形参中的name值赋给this指向的new出来的新的name空间`



> 作用

1、可以分局部变量和成员变量同名的问题

2、代表的是当前对象的引用。谁来调用我，我就指向谁。

3、this();代表的是当前类中的其他构造方法。

4、也可以调用当前类的成员方法



*使用实例*

```java
package com.ydlclass;

public class Car {
    String name;
    String color;
    long length;

    //无参构造
    public Car(){
        //this当构造器 ，只能放在第一行	创建好了才能干活 
        this("benz", "black",1000);
    }
    //有参调用
    public Car(String name, String color, long length){
        this.name = name;
        this.color = color;
        this.length = length;
        this.run();
        System.out.println("成功调用有参构造");
    }
    //跑起来了
    public void run(){
        System.out.println("跑起来了！");
    }

    public static void main(String[] args) {
        Car bmw = new Car();
        System.out.println(bmw.name);

    }
}

```

### 7、getter和setter

getter方法用来获取成员变量的值；

setter方法用来给成员变量赋值；

```java
package com.ydlclass.entity;

public class Girl {
    private String name;
    private int age;


    public static void main(String[] args) {
        Girl girl1 = new Girl();
        girl1.age = 56;
        System.out.println(girl1.age);
    }

    //get+set

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

```

为什么呢？

- getter方法能够按照客户的期望返回格式化数据。
- setter方法可以限制和检验setter方法传入的参数，隐藏对象内部数据结构。
- 属性不具备多态性。



> 现在的标准代码

下方代码写入entity，main方法写入test中

```java
package com.ydlclass.entity;

public class Girl {
    //第一块：成员变量
    private String name;
    private int age;

    //第二块：构造器
    public Girl(){//权限可修饰

    }

    //第三块：成员方法
    public void chiFan(){
        System.out.println("吃饭啦！");
    }

    //第四块：get+set
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}


```



### 8、String详解

#### (1)**String是引用数据类型**

```java
String name = new String("name");

String name = "name";//语法糖

```



> String的问题

```java
String s1 = "123";
String s2 = "123";
System.out.println(s1 == s2);
//输出结果是true
//因为"123"放进常量池中，所以两个引用都是指向同一个位置，所以相等
//基础数据类型的值不在常量池中放，直接放进槽中
//系统会认为定义的字符串以后还会使用，所以放进常量池

```

```java
s1 = new String("abc");
s2 = new String("abc");
System.out.println(s1 == s2);
//输出结果是false
//new是在堆内存新创建空间 ，虽然创建的空间指向常量池中的"123"，是两片不同的空间，所以s1、s2各自指向各自new出来的空间

```

```java
String s3 = "abc" + "bcd";
System.out.println(s3);
//创造三个对象，三个对象分别在内存空间中存在

```

#### (2)**String构造应知应会**

- 知道String创建 的时候可以使用byte数组、字符串数组可以直接定义
- 直接定义是放进常量池中
- new的话会在堆内存中创建空间

#### (3)**String常用方法**-Test2.java

String是引用数据类型，所以创建下就是一个对象，就会有方法

```java
package com.ydlclass.test;

import java.nio.charset.StandardCharsets;
import java.util.Locale;

public class Test2 {


    public static void main(String[] args) {
        String str = "bHelloa World";
        //转成数组，输出第一个元素的值
        System.out.println(str.getBytes(StandardCharsets.UTF_8)[0]);
        //输出小写
        System.out.println(str.toLowerCase());//变成小写
        //输出大写
        System.out.println(str.toUpperCase());//变成大写

        //输出的是方法的返回值,如果没有这个字符串就返回-1
        System.out.println(str.indexOf("World3"));//下标在哪里

        //8是开始的下标，10是结束的下标，如果只有8是从8开始输出
        System.out.println(str.substring(8, 10));

        //替换
        System.out.println(str.replaceAll("oa", "ao"));//替换

        //输出当前下标的值
        System.out.println(str.charAt(3));
        //检测是否包含
        System.out.println(str.contains("He"));
        //str并没有被改变
        System.out.println(str);
    }
}

```



#### (4)**屏蔽细节、暴露方法、封装对象**

#### (5)转义符-StringEscape.java

```java
package com.ydlclass.test;

public class StringEscape {
    public static void main(String[] args) {
        // \转义符
        String str = "abc\\\"abc\"abc";
        System.out.println(str);
    }
}

```

#### (6)单词出现的次数

```java
package com.ydlclass.test;

import java.nio.charset.StandardCharsets;
import java.util.Locale;

public class Test2 {


    public static void main(String[] args) {
        String str = "Hello World abc Hello";
        //转成数组，输出第一个元素的值
/*        System.out.println(str.getBytes(StandardCharsets.UTF_8)[0]);
        //输出小写
        System.out.println(str.toLowerCase());//变成小写
        //输出大写
        System.out.println(str.toUpperCase());//变成大写

        //输出的是方法的返回值,如果没有这个字符串就返回-1
        System.out.println(str.indexOf("World3"));//下标在哪里

        //8是开始的下标，10是结束的下标，如果只有8是从8开始输出
        System.out.println(str.substring(8, 10));

        //替换
        System.out.println(str.replaceAll("oa", "ao"));//替换

        //输出当前下标的值
        System.out.println(str.charAt(3));
        //检测是否包含
        System.out.println(str.contains("He"));
        //str并没有被改变
        System.out.println(str);*/
        Test2 test2 = new Test2();
        int var = test2.wordCount(str, "hello");
        System.out.println(var);

    }
    //成员方法
    public int wordCount(String article, String word){
        int res = 0;
//        article.toUpperCase();
//        word.toUpperCase();
        //先把字符串根据空格隔开
        String[] str = article.split(" ");
        for (int i = 0; i < str.length; i++) {
            if(str[i].equalsIgnoreCase(word)){
                res++;
            }
        }
        return res;
    }
}

```



### 9、包装类和拆装对象

平时对基础数据类型进行一些操作，因为基础类型没有类，不好操作。

Java堆基础数据类型进行的封装，生成对应的包装类。

包装类不仅有方法，还有一个特殊值null

| 基本数据类型 | 包装类    |
| :----------- | :-------- |
| byte         | Byte      |
| boolean      | Boolean   |
| short        | Short     |
| char         | Character |
| int          | Integer   |
| long         | Long      |
| float        | Float     |
| double       | Double    |

```java
Integer num = new Integer(12);//比较麻烦的定义

//Integer也能代表一个基础数据类型
Integer num = 12;//12是基础数据类型，Integer是包装类，系统进行的把基础类型变成一个包装型这种自动转换，叫做包装类——对12进行了自动装箱

//
long l = new Long(12L);//把一个包装类赋值给一个基础数据类型，叫做拆装类

```



### 10、封装一个超级数组——7.2开的

```java
package com.ydlclass.homework.entity;

import java.nio.charset.StandardCharsets;

/**
 * 超级数组
 * 想用数组的方式区存储一些数据，但是又想规避它实现的细节，
 * 这就是封装的好处，叫隐藏实现的细节，暴露我需要的方法
 */
public class SuperArray {

   //定义成员变量
    private int[] nums;
    private int currentIndex = -1;
    private int capacity;
    //构造方法
    public SuperArray(){
        this(10);
    }
    public SuperArray(int capacity){
        nums = new int[capacity];
        this.capacity = capacity;
    }
    //增加
    public void add(int data){
        currentIndex++;
        int[] temp = new int[nums.length+1];
        for (int i = 0; i < nums.length; i++) {
            temp[i] = nums[i];
        }
        temp[currentIndex] = data;
        nums = temp;
    }
    //尾插
    //10000个数据，110ms
    public void addTile(int data) {
        this.addIndex(currentIndex + 1, data);
    }

    //头插
    public void addHead(int data) {
        this.addIndex(0, data);
    }
    //增加指定位置
    public void addIndex(int index, int data){
        int[] temps = new int[nums.length+1];
        for (int i = 0; i < nums.length; i++) {
            temps[i] = nums[i];
        }
        for (int i = currentIndex; i >= index; i--) {
            temps[i+1] = temps[i];
        }
        temps[index] = data;
        nums = temps;
        currentIndex++;
    }

    //删除
    public void delete(int index){
        if(this.testIndex(index)){
        } else {
            for (int i = index; i < currentIndex; i++) {
                nums[i] = nums[i+1];
            }
            currentIndex--;
            System.out.println("成功删除");
        }
    }

    //查找
    public Integer set(int index){
        if(this.testIndex(index)){
            return null;
        } else {
            return nums[index];
        }
    }

    //改
    public void changeArray(int index, int data){
        if(testIndex(index)){

        } else {
            nums[index] = data;
        }
    }
    //遍历
    public String arrayToString(){
        String str = "[";
        for (int i = 0; i <= currentIndex; i++) {
            str += nums[i]+ ",";
        }
        return str.substring(0, str.length()-1) + "]";

    }
    //数组有效数据
    public int size(){
        return currentIndex+1;
    }

    //检测下标是否越界
    public boolean testIndex(int index){
        if(index < 0 || index > currentIndex){
            System.out.println("输入的下标[" + index +"]越界了");
            return true;
        } else {
            return false;
        }
    }

    public void sort(){
        for (int i = 1; i < currentIndex+1; i++) {
            for (int j = 0; j < currentIndex+1-i; j++) {
                if(nums[j] > nums[j+1]){
                    int t = 0;
                    t = nums[j];
                    nums[j] = nums[j+1];
                    nums[j+1] = t;
                }
            }
        }
    }

}


```



### 11、封装一个超级链表-7.4

- 又是一个新的名词：链表
- 在内存空间中，数组和链表都是基本的数据结构，都是【表】，或者叫【线性表】。
- 线性表是一个线性结构，它是一个含有n≥0个结点的有限序列，对于其中的结点，有且仅有一个开始结点没有前驱但有一个后继结点，有且仅有一个终端结点没有后继但有一个前驱结点，其它的结点都有且仅有一个前驱和一个后继结点，说人话，就是有头有尾一条线。

![image-20210722113751650](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210722113751650.png)

**抽离共同的代码，让他们服务于我们暴露的方法**

```java
package com.ydlclass.entity;

public class SuperLink {

    private Node head;
    private int currentIndex = -1;

    //增加
    public void add(int index, int data) {
        if (head == null) {
            head = new Node(data, null);
        } else {
            if (index == 0) {
                Node newNode = new Node(data, head);
                head = newNode;
            } else {
                Node node = selectNode(index-1);
                Node newNode = new Node(data, node.getNext());
                node.setNext(newNode);
            }
        }
        currentIndex++;
    }

    //尾插
    public void addHead(int data){
        this.add(currentIndex+1, data);
    }
    //头插
    public void addTile( int data){
        this.add(0, data);
    }
    //删除
    public void delete(int index) {
        if(index == 0){
            Node newNode = head.getNext();
            head = newNode;
        } else {
            //找到index-1的节点
            Node node = selectNode(index-1);
            node.setNext(node.getNext().getNext());
        }
        currentIndex--;
    }

    //查找
    public int lookUp(int index) {
        return selectNode(index).getData();
    }

    public void change(int index, int data) {
        if (index == 0) {
            Node newNode = new Node(data, head.getNext());
            head = newNode;
        } else {
            Node node = selectNode(index);
            Node newNode = new Node(data, node.getNext());
            node.setNext(newNode);
        }
    }

    //遍历
    public String arrayToString() {
        String str = "[";
        for (int i = 0; i < currentIndex + 1; i++) {
            str += lookUp(i) + ",";
        }
        return str.substring(0, str.length() - 1) + "]";
    }

    //返回index节点的查找
    private Node selectNode(int index){
        Node node = head;
        for (int i = 0; i < index; i++) {
            node = node.getNext();
        }
        return node;
    }

}

```



### 12、封装一个栈(盖房子的砖)和队列(排队买东西)

栈（Stack）和队列（Queue）是两种操作受限的线性表。

这种受限表现在：栈的插入和删除操作只允许在表的尾端进行（在栈中成为“栈顶”），满足“FILO：First In Last Out”；队列只允许在表尾插入数据元素，在表头删除数据元素,满足“First In First Out”。

栈与队列的相同点：

1. 都是线性结构。
2. 插入操作都是限定在表尾进行。
3. 都可以通过顺序结构和链式结构实现。

栈与队列的不同点：

1. 队列先进先出，栈先进后出。

#### jar

指定模块生成jar，在需要使用jar的java文件中添加jar

#### 栈

```java
package com.ydlclass;

import com.ydlclass.homework.entity.SuperArray;

public class Stack {

    private SuperArray superArray = new SuperArray();
    //压栈 从头进入
    public void add(int data){
        superArray.addHead(data);
    }
    //从尾巴上输出
    public int pop(){
        Integer set =  superArray.set(0);
        superArray.delete(0);
        return set;
    }
}

```

#### 队列

```java
package com.ydlclass;

import com.ydlclass.homework.entity.SuperArray;

public class Queue {
    private SuperArray superArray = new SuperArray();
    //入队 从头进入
    public void push(int data){
        superArray.addHead(data);
    }
    //从尾巴上输出
    public int pop(){
        Integer set = superArray.set(superArray.size()-1);
        superArray.delete(superArray.size()-1);
        return set;
    }
}

```

### 13、银行取票机小系统

```java
package com.ydlclass;

import com.ydlclass.homework.entity.SuperArray;

import java.util.Scanner;

public class BackTicket {
    //成员属性
    private Queue queue = new Queue();
    private String currentName = null;

    //成员方法
    //系统在票机中加号，然后输出票号
    public void getTicket(){
        while(true){
            if(queue.isEmpty()){
                for (int i = 0; i < 10; i++) {
                    queue.add(i);
                }
            }
            this.getName();
            System.out.println("您好，"+currentName+"您的号为："+queue.push());
        }
    }
    //获取用户的名字
    private void getName(){
        System.out.print("请输入您的名字：");
        Scanner scanner = new Scanner(System.in);
        currentName = scanner.next();
    }

    //启动
    public void start(){
        while(true){
            this.getTicket();
        }
    }
}

```

```java
package com.ydlclass;

import java.util.Scanner;

public class Back {
    public static void main(String[] args) {

        BackTicket backTicket = new BackTicket();

        backTicket.start();
    }
}

```

## 三、面向对象之继承——inherit

提出需求来思考：

我想创建一个学生类，男学生类，女学生类，会有这么几个问题：

1、不管是男同学还是女学生，都是学生，学生公有的方法和属性本来就有很多。

2、虽然都是学生，但是男女毕竟有别，还是有一些不一样的地方。

在以往的认知当中，我们不得不创建学生类，男学生类，女学生类，然后书写每一个重复的属性和方法。

但是java给我们提供了更好的解决方案叫继承。



### 1、基本介绍——extends

​		继承可以解决代码复用的问题，一个类可以继承一个类，被继承的类我们称之为【父类】或者【超类】，另一个类称之为【子类】也叫【派生类】，子类可以通过extends关键字轻松拥有获取父类的成员变量和成员方法的能力，除了被private修饰的。在java中是单继承的，这样可以规范代码的实现。  

​		继承其实很好理解的，我们天生就会继承来自父母的很多基因，那爸爸的很多能力或者特征你天生就会拥有。

![image-20210803142249085](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210803142249085.png)

so，设计一个Father类，两个Son类，以一个SonOne，一个SonTwo，儿子类可以继承父亲类的方法，也可以有自己独立的方法

```java
public class Father {
    private String name;

    public void eat() {
        System.out.println("吃了");
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

```java
public class SonOne extends Father{
    public void play(){
        System.out.println("玩起来了")
    }
}

```

```java
public class SonTwo extends Father{
}	

```

```java
public class Test {
    public static void main(String[] args) {
        SonOne sonOne = new SonOne();
        sonOne.setName("张三");
        System.out.println(sonOne.getName());
        sonOne.eat();
    }
}

```

![image-20210803164839552](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210803164839552.png)

### 2、解释

- 自己依然是自己，是继承了父类、爷爷类的方法，自己也有自己的方法
- 先去类中找，找不到去父类，再找不到去爷爷类

### 3、super关键字

- 构建子类的时候，一定会先创建父类



它的作用有以下几个：

- 在子类的成员方法中，访问父类的`成员变量`。
- 在子类的成员方法中，访问父类的`成员方法`。
- 在子类的构造方法中，访问父类的`构造方法`。

```java
Father叫父亲
Son叫儿子
GrandSon叫孙子
   孙子有个方法是play System.out.println(super.name+"玩起来了");
输出的是儿子玩起来了

```

1. 子类继承了父类所有的非私有的属性和方法，可以直接调用。
2. 子类在构造的时候，一定会构造一个父类，默认调用父类的无参构造器。
3. 子类如果希望指定去调用父类的某个构造器， 则显式的调用一下 : super(参数列表)
4. super和this当做构造器使用时， 必须放在构造器第一行，所以只能二选一。
5. java 所有类都是 Object 类的子类, Object 是所有类的基类.
6. 子类最多只能继承一个父类(指直接继承)， java 中是单继承机制，我们可以使用连续继承来实现。

### 4、super和this区别

- this调用同类的方法
- super调用父类的方法
- 不能同时使用
- super和this当构造器使用时之前都不能有语句

|            | this                                           | super                                          |
| ---------- | ---------------------------------------------- | ---------------------------------------------- |
| 访问属性   | 访问本实例的属性，没有会继续向父类检索         | 访问父类实例的属性，没有会继续向父类检索       |
| 调用方法   | 访问本实例的方法，没有会继续向父类检索         | 访问父类实例的方法，没有会继续向父类检索       |
| 调用构造器 | 调用本类的构造器，必须放在第一行，不会向上检索 | 调用父类的构造器，必须放在第一行，不会向上检索 |



### 5、方法重写@Override注解——告诉别人这个方法是重写的方法

子类可以继承父类的方法，但是所有的方法的方法不能跟父类一样，在那个会有些变化，龙生九子，各有不同

就带来了方法重写，子类的方法重写必须要跟父类的方法签名相同，同样的名字，同样的形参列表

确定一个方法使用方法签名确定的

|                  | 范围   | 方法名   | 形参列表                           | 返回类型                                   | 权限修饰                   |
| ---------------- | ------ | -------- | ---------------------------------- | ------------------------------------------ | -------------------------- |
| 重载（overload） | 本类   | 必须一样 | 类型，个数或者顺序不同，名字无所谓 | 没有要求                                   | 无要求                     |
| 重写（override） | 父子类 | 必须一样 | 必须相同                           | 一样，或者子类的返回值是父类的返回值的子类 | 子类不能缩小父类的访问权限 |



| 作用域                      | 当前类 | 同package | 子孙类                    | 其他package |
| --------------------------- | ------ | --------- | ------------------------- | ----------- |
| public(公共的)              | √      | √         | √                         | √           |
| protected(受保护的)         | √      | √         | √                         | ×           |
| friendly( default )(友好的) | √      | √         | ×(同包下的子孙类可以使用) | ×           |
| private(私有的)             | √      | ×         | ×                         | ×           |

- default只能在同包下的子类中使用，如果子类跟父类不在一个包，父类的方法无修饰符或者使用default，子类就不可以使用父类的方法
- 其实平常使用的就是三个：public(公共的)、private(只能自己用)、protected(让子孙类使用)、

### 6、final关键字

- String类型的数据被final修饰之后，内容是不能被改变的
- final不止能够修饰String，还能修饰方法、变量、成员变量、局部变量、类上
  - final修饰的类不能被继承；
  - final修饰的方法不能被重写；
  - final修饰的基础数据类型的值不能改变，引用数据类型的引用地址中的内容可以改变，但是引用的地址不可以改变；



### 7、祖先类——Object

| 方法                               | 描述                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| boolean equals(Object obj)         | 指示某个其他对象是否与此对象“相等”                           |
| public native int hashCode();      | 返回该对象的哈希码值                                         |
| String toString()                  | 返回该对象的字符串表示                                       |
| Class<? extendsObject> getClass()  | 返回一个对象的运行时类                                       |
| void notify()                      | 唤醒在此对象监视器上等待的单个线程                           |
| void notifyAll()                   | 唤醒在此对象监视器上等待的所有线程                           |
| void wait()                        | 导致当前的线程等待，直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法 |
| void wait(long timeout)            | 导致当前的线程等待，直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法，或者超过指定的时间量 |
| void wait(long timeout, int nanos) | 导致当前的线程等待，直到其他线程调用此对象的 notify()        |
| protected native Object clone()    | 克隆对象，浅拷贝                                             |
| protected void finalize()          | 垃圾回收器准备释放内存的时候，会先调用finalize()。           |



#### (1)hashcode()

这个方法是这么定义的，所有带有native的方法都是本地方法，它不是java写的。这个hashcode的返回值其实是实例对象运行时的内存地址。

本地的代码是用c++实现的

```
public native int hashCode();

```

什么是hash算法：

​        一般翻译做“散列”，也有直接音译为“哈希”的，就是把任意长度的输入（又叫做预映射， pre-image），通过散列算法，变换成固定长度的输出，该输出就是散列值。

hash算法有几个特点：

1、只能通过原文计算出hash值，而且每次计算都一样，不能通过hash值计算原文。

2、原文的微小变化就能是hash值发生巨大变化。

3、一个好的hash算法还能尽量避免发生hash值重复的情况，也叫hash碰撞。

hash算法的主要用途

1、密码的保存

实际的工程当中我们一般不存储明文密码，而是将密码使用hash算法计算成hash值进行保存。这样即使密码丢失也不会使密码完全曝光。

![image-20210816151639948](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210816151639948.png)

输入的密码通过md5算法变成散列保存在数据库中，只能顺着推，不能逆着推

登录的时候是通过用户名查找数据库中的散列密码，然后将输入的密码通过md5算法散列出进行对比

找回密码是验证是本人之后，用新的密码散列覆盖之前的密码散列

2、文件的检验、检查数据的一致性

![image-20210816152722879](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210816152722879.png)

把下载的文件通过hash算法计算出结果，然后从官网得到正确的hash值进行比较，如果一直就是正确的文件，否则就是错误的文件，微小的变动就会引起结果巨大的变化

#### (2)equals()

equals重写

```java
package com.ydlclass;

public class Student {
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public boolean equals(Object object){
        Student student = (Student) object;
        return student.getAge() == this.getAge() && student.getName().equals(this.getName());
    }
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

}

```

[重要总结]：

- ==可以比较基础数据类型和引用数据类型，基础数据类型比较的是值，引用数据类型比较的是引用地址，
- equals是object方法，默认的实现是==
- 我们可以根据自己的特殊要求重写equals方法，比如String就重写了equals方法，字符串调用equals方法比较的是每个字符

#### (4)toString()

- System.out.println输出的时候默认调用toString方法，一般的实例对象输出的是地址，但是String重写了toString方法，输出的是内容

#### (5)finalize()

不稳定、不可靠、不推荐使用

#### (6)clone()

浅克隆，简单一点就是说复制了一个一样的指针



## 四、面向对象之多态——polymorphism-7.6-父类引用可以指向子类对象

### 1、概述

**调用方法的时候调用的是传入对象类型的方法**

我们在很多网站上可以看到对于多态的形成条件有以下三个条件：

1、有继承

2、有重写

3、有父类引用指向子类对象

这种说法在宏观上是正确的，接下来我们就去探究一下具体的调用逻辑，或许你会大吃一惊。

```java
Pet dog = new Dog();//父类引用指向子类对象

girl.feed(dog);//形成多态
				//feed方法的形式参数是父类，调用方法传入的实参是子类

public void feed(Pet pet){//为什么是父类、为什么会重写
        pet.coquetry();
    }

```



### 2、多态的底层原理-多态再方法调用中的本质

#### (1)字节码分析(11-3视频)——三刷

运行二进制文件是在out文件夹中找到class文件，然后使用np++打开，或者javap -v 类名.class

```java
Animal animal = Math.random() > 0.5 ? new Dog():new Cat(); 

```

- 对于animal来说，到底是个Dog类型还是Cat类型是不确定的，都有50%的概率，只有运行的时候才知道时什么类型
- 我们叫Animal为【静态类型】、【编译类型】、【申明类型】、【外观类型】
- Dog、Cat叫做【动态类型】、【运行时类型】、【实际类型】

![image-20210818114754607](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210818114754607.png)

常量池(资源仓库)：定义了一些字符串，保存了大量的符号引用：自己定义的字符串、方法的名字(程序没有运行是不知道方法保存的地址的，所以使用符号代替)、类的名字、包的名字、父类的名字……

#### (2)方法在栈帧中的调用

先是main方法压入栈帧，然后按照调用方法的顺序进行压栈，最后弹栈。

内存中有个栈区，栈区中有很多方法栈，每个方法栈又有自己的逻辑(操作数栈)

操作数栈是用来告诉内存分配空间的，栈深度是压入几个数据

![image-20210818132422744](../%E4%B8%8B%E8%BD%BD/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1.assets/image-20210818132422744.png)

```java
public int plus(int, int);
    descriptor: (II)I
    flags: ACC_PUBLIC
    Code:
	  // 这里告诉你操作数栈深度为2，本地变量有3个，参数有三个
      stack=2, locals=3, args_size=3
         0: iload_1
         1: iload_2
         2: iadd
         3: ireturn
      LineNumberTable:
        line 6: 0
      // 本地变量表，很明显这里有三个，this 、 i、 j，我们可以画图解析一下这个过程，如下图
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       4     0  this   Lcom/ydlclass/Computer;
            0       4     1     i   I
            0       4     2     j   I

```

```java
//后面的注释在二进制文件中可以看见
public class Computer(){
    String name;
    Computer computer = new Computer();
    computer = new zilei();
    sout(computer.play());//这里调用的play方法就是子类的方法了，这种方法在编译的时候是不知道具体的方法的。只有在运行的时候才知道具体的方法，这就是虚方法，指令就是invokevirtual指令的虚指令，这就是多态
    //虚方法调用：需要进行方法版本选择的选择具体的方法调用对象，选择具体的调用者或者具体的调用方法的版本，这种过程就叫做分派
    //有静态的invokespecial指令，编译的时候就知道调用的是什么方法，比如构造方法
    //不被pritive、final修饰的方法都是虚方法
    //栈顶指向的对象(有可能是本类对象，也有可能是子类对象)的方法，如果没有就从下至上(父类)寻找方法，这个过程就是动态分派，只在运行的时候才可以进行选择，平时的时候选择不了
}

```

```java
public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: ACC_PUBLIC, ACC_STATIC
    Code:
      stack=4, locals=2, args_size=1
      	 // 创建一个对象，并将其引用值压入栈顶
         0: new           #2                  // class com/ydlclass/Computer
         // 复制栈顶数值并将复制值压入栈顶
         3: dup
         // 很明显这是在调用构造器，编译之后还是符号引用，就是方法的字符串形式的名字，
         // 加载之后，我们就可以解析成对应的方法的调用地址了
         // 因为一旦类加载到内存的方法区，这个方法就有了真实的调用地址了
         4: invokespecial #3                  // Method "<init>":()V
         // 将栈顶引用型数值存入第二个本地变量
         7: astore_1
         // 获取指定类的静态域，并将其值压入栈顶
         8: getstatic     #4                  // Field java/lang/System.out:Ljava/io/PrintStream;
         // 将第二个引用类型本地变量推送至栈顶
        11: aload_1
        // 将 int 型 2 推送至栈顶
        12: iconst_2
        // 将 int 型 4 推送至栈顶
        13: iconst_4
        // 调用实例方法，调用的过程是在内存进行的，只有当字节码被加载进入内存才有具体的地址
        14: invokevirtual #5                  // Method plus:(II)I
                 
                  // 以下部分是粘贴过来的plus方法的，此时会创建新的栈帧
                  // 单独这个方法的指令入口在编译的时候是不可知的，但是加载到内存就可知了
                  // 其实，这个调用的不一定是这个方法，只是为了演示
                 -------------------------
                 // 将第二个 int 型本地变量推送至栈顶
                 0: iload_1
                 // 将第三个 int 型本地变量推送至栈顶
                 1: iload_2
                 // 将栈顶两 int 型数值相加并将结果压入栈顶
                 2: iadd
                 3: ireturn 
             	 -------------------------   
        17: invokevirtual #6                  // Method java/io/PrintStream.println:(I)V
        20: return
      LineNumberTable:
        line 10: 0
        line 11: 8
        line 12: 20
      LocalVariableTable:
        // 这里的Signature就是一个引用的静态类型，这里早有记录
        Start  Length  Slot  Name   Signature
            0      21     0  args   [Ljava/lang/String;
            8      13     1 computer   Lcom/ydlclass/Computer;
}

```



#### (3)重载方法(静态的多态)的调用

```java
package com.ydlclass;

public class Party {

    public void play(Human human){
        System.out.println("人类的狂欢！");
    }

    public void play(Man man){
        System.out.println("男人的狂欢！");
    }

    public void play(Woman woman){
        System.out.println("女人的狂欢！");
    }

    public static void main(String[] args) {
        Party party = new Party();
        Human human = new Human();
        party.play(human);
        Human man = new Human();
        party.play(man);
        Human woman = new Human();
        party.play(woman);
    }
}

```

- 虚拟机选择重载方法的时候是根据静态类型进行选择的
- 这里的重载的play方法会根据传入的实参的类型进行选择，这里的human、man、woman都是Human类型的数据，所以输出都是人类在狂欢
- 传给play方法的man是用Human类型修饰的，虚拟机就会认为调用的是Human的play方法
- 和给他的什么类型的对象没关系，有关系的是这个对象是用什么数据类型修饰的

![image-20220706215100191](%E5%9B%BE%E7%89%87/image-20220706215100191.png)

#### (4）重载和重写的综合案例

```java

```

第一步：静态分派，jvm从Animal类的多个重载方法中选择了eat(String food)这种方法，并且生成指令`invokevirtual Animal :: eat(String food)`

第二步：动态分派，根据运行时确定具体调用谁的eat(String food)，应为运行时类型是Dog，所以最终选择的方法是`Dog :: eat(String food)`

就是先让jvm进行静态分派，确定使用哪种重载版本的方法，然后根据运行时候的引用的具体实例对象的类型决定使用哪个重载方法



多态只和方法有关，和属性无关

```java
Animal和Dog都要有一个公开的name属性
Animal animal = new Dog();
sout("animal.name");//输出的是Animal的名字，因为属性不参与多态
//因为在jvm编译的时候，就已经知道Animal的所有属性了，不知道Dog的属性

```

### 3、对象的转型

- 向上转型：子类对象转成父类，向上转型不需要显示的转化，`Father father = new Son();`向上转型会丢失子类独有的属性
- 向下转型：父类对象转为子类，向下转型需要强制类型转换，`Son son = (Son)new Father;`向下转型可能会出现错误

```
package com.ydlclass;

public class Girl {
    //实参传过来就进行了自动向上转型
    public void feed(Pet pet){
        pet.coquetry();
        if(pet instanceof Dog){
            //手动进行向下转型
            Dog dog = (Dog)pet;
            ((Dog) pet).run();
        }
        if(pet instanceof Cat){
            Cat cat = (Cat)pet;
            cat.play();
        }
    }

    public static void main(String[] args) {
        Girl girl = new Girl();
        girl.feed(new Cat());
    }
}

```

### 4、抽象类和接口-7.7

抽象：很多的概念都是抽象出来的，概念不是具体的事件本身，而是抽象出来的一些规律

接口：水缸上面有接口

#### (1) 抽象方法和抽象类的定义——abstract

抽象方法是抽象出来的一种概念

我们把老虎、狮子、骆驼等动物抽象出来一个具体的类——动物类，吃这个方法也应该抽象出来成为一种行为

- 有抽象方法的以一定使用`absoract`进行修饰为抽象类
- 继承自抽象类的子类要么也是抽象类，要么实现抽象类的所有的抽象方法

#### (2)接口的定义——interface(接口)、implements(实现)

如果一个类中全部都是抽象方法，那么就可以把这个类转成接口

其中的抽象方法可以不写权限修饰符，默认是public，只能是public

**接口是多实现的，一个类可以实现多个接口，只能继承一个类，接口之间可以相互继承**

#### (3)深入理解

- 继承：is a的关系，狗是动物、猫是宠物
- 实现：can do的关系，狗可以实现动物的行为、猫可以实现动物的行为，可以多实现
- 抽象类是模板式设计，相同的能力定义成公用的(狮子和狗都会叫)，不同的行为可以定义成抽象的(狮子吃肉狗吃屎)，
- 实现是契约式设计就是约定所有的子类都可以实现的行为，只要实现接口就拥有这个能力
- 抽象类就是将所有的实现方法定义到父类，不同的在子类实现
- 接口是规定，是契约，是规范所有实现这个接口的类都拥有的能力

比如今年主抓教育，然后各个县进行自己的安排，就是抽象了一个抓教育接口，每个县拥有自己的实现

### 5、设计模式—理解在顶层设计是干什么的

为了解决相同的表征问题的解决方案

#### (1)面向对象设计原则

##### a.开闭原则(Open Close principle)

**对扩展开放，对修改关闭**

##### b.里氏替换原则(Liskov Substitution Principle)

继承的时候尽量不要重写父类的方法，如果需要重写，把父类设成抽象的

##### c.依赖倒转原则(Dependence Inversion Principle)

面向接口编程，不要面向实现编程

##### d、接口隔离原则（Interface Segregation Principle）

尽量把大的接口拆分成更小、更具体的接口

##### e、迪米特法则（最少知道原则）（Demeter Principle）

如果两个实例对象无需直接通信，那么就不应该发生直接的相互调用，那么就可以通过第三方转发该调用，戳还是为了低耦合，提高模块的相对独立性

比如买东西，买家找个卖家，就需要买家持有一个卖家，传入一个卖家，如果有个第三方平台来进行沟通，就会低耦合

##### f、合成复用原则（Composite Reuse Principle）

##### g、单一原则

一个类只做一件事情，面包房就只做面包



`写个对象，写个接口，让对象实现接口`



## 五、面向对象的其他知识7.8

### 1、代码块

代码块又称为初始化块，属于类中的成员，它是将逻辑语句包装在方法体中，通过{}包裹。代码块没有方法名，没有参数、没有返回值、只有方法体，而且不通过对象或类进行显示的调用，他会在类加载，或者创建对象时主动的隐式调用。

#### (1)静态代码块

一个类被加载时会被调用一次，常用在需要做一些全局初始化的工作。

类会在第一次主动调用的时候被加载到内存中，new的时候或者创建子类的时候会创建父类

```java
static{
    
}

```

#### (2)实例代码块

每次创建实例，都会被调用 一次，其实用的很少，因为阅读性不强，一般直接写入构造器

new对象的时候，调用构造器的时候

如果在class文件中看的时候，实例代码块的内容在无参构造中，如果无参构造中有内容，实例代码块的优先级在其之前

```java
{

}

```

#### (3)执行顺序

先加载父类，再加载子类，输出静态；

构造子类的时候先构造父类，实例代码块都会在构造方法中，而且优先级高，输出实例+构造方法

```java
父静、子静、父实、父构、子实、子构
实例代码块和构造器虽然分开写的，但是会编译进构造器中

```

```java
package com.ydlclass.block;

public class Father {
    public Father(){
        System.out.println("父类的构造器");
    }
    static {
        System.out.println("父类的静态代码块");
    }
    {
        System.out.println("父类的实例代码块");
    }
}

```

```java
package com.ydlclass.block;

public class Son extends Father{
    public Son(){
        System.out.println("儿子的构造器");
    }
    {
        System.out.println("儿子的实例代码块");
    }
    static {
        System.out.println("儿子的静态代码块");
    }

    public static void main(String[] args) {
        new Son();
    }
}
//输出
父类的静态代码块
儿子的静态代码块
父类的实例代码块
父类的构造器
儿子的实例代码块
儿子的构造器

```



### 2、静态方法和静态变量

```java
package com.ydlclass.block;

public class Test2 {
    /**
     * 静态变量在方法区，在编译好的字节码文件中，yal保存在常量池中
     * 会主动的创建一个静态代码块，
     * 执行这个赋值的过程，静态代码块在执行这个类的时候就会执行
     * 如果在main中重新赋值是改变常量池中的内容不是改变引用
     */
    public static String name1 = "ydl";
    public String name2 = "ydlclass";
    public static  void print(){//静态方法
        System.out.println("hello");
    }

    public static void main(String[] args) {
        Test2.name1 = "zhangsan";
        System.out.println(Test2.name1);//静态变量怎么拿 类名.静态变量名
        Test2.print();
    }
}

```

#### 1、我们应该知道：

> - 静态变量和静态方法是保存在方法区中的，其他方法也在方法区
> - 他们不是实例对象，只存在在方法区，如果使用的话是类名.静态方法/类名.静态变量

#### 2、用途：

- 静态方法通常作为一些无状态(不操作状态)的方法，做一些工具性的类util
- 进行一些工具类的封装，就是调用一下，完成一下功能，使用静态方法
- 进行对象状态(属性)的操作需要使用实例方法，new一个对象然后.方法
- 静态变量的值就是一样的，不管多少个类进行使用，都是一样的值
- 用static final进行静态常量的声明，静态常量字母全部大写使用下划线分开，经常使用的数据，使用final是防止别人修改 



#### 3、实例方法和静态方法的区别

> - 静态的方法不可以调用非静态的方法，因为非静态的是实例方法，需要new对象
> - 实例对象可以相互调用是因为this、super
> - 如果在静态方法中调用实例方法，必须要new一个实例对象

其实我们应该明白：

- 在Java中调用实例方法必须要有个主体，new一个对象
- 在同一个类中实例方法相互调用可以以省略this，在`静态方法中没有this`，在静态方法中调用实例方法必须new一个对象
- 调用静态方法都是`类名.方法名`调用，一个类加载到方法区中，它的静态方法就已经进入方法区了，静态变量也转成一个静态代码块进行赋值了
- 实例方法是用来操作实例对象的属性(状态)

### 3、内部类、静态内部类

- 外部类有的东西内部类都有
- 内部类如果不加static就只属于实力对象，只能先new一个外部类，再new一个内部类 `new Outer().new Inner()`
- 如果加了static就可以`new Outer.Inner();//静态方法的使用`

```java
package com.ydlclass.block;

public class Outer {

    //构造器
    public Outer(){
        System.out.println("outer");
    }
    //内部类
    public class Inner {//没有加static就是属于实例对象的，需要new内部类就得new Outer().new Inner(); 
        public Inner(){
            System.out.println("inner");
        }
    }
    //实例方法
    public void test(){
        new Inner();
    }


    public static void main(String[] args) {
        new Outer().test();
    }
}

```

`new Outer.Inner();`

静态内部类的好处就是可以只加载一次，加载多了不好

```java
package com.ydlclass.block;

public class Outer {

    //外部的构造器
    public Outer(){
        System.out.println("outer");
    }

    //方法
    public void test(){
        new Inner();
    }

    //内部类
    private static class Inner{//只有在调用Inner的时候才会输出一次
        public Inner(){
            System.out.println("inner");
        }

    }

    public static void main(String[] args) {
        //构造的时候Outer类就会加载，就会输出outer
        Outer outer = new Outer();

        //调用方法的时候就会new一个Inner，Inner加载，使用构造方法，输出inner
        outer.test();
    }
}

```



### 4、单例设计模式

`这个类只能有一个实例对象`

#### (1)饿汉式

```java
package com.ydlclass.singLeton;

public class Singleton {
    //静态私有属性，类加载的时候就new了，就很着急，饿汉式
    private static final Singleton INSTANCE = new Singleton();

    //构造器私有化，不能让别人new
    private Singleton(){

    }

    //公共的静态方法，可以直接使用类名调用，返回实例
    public static Singleton getInstance(){
        return getInstance();
    }
}

```



#### (2)懒汉式

```java
package com.ydlclass.singLeton;

public class Singleton {
    //静态私有属性
    private static Singleton INSTANCE;

    //构造器私有化，不能让别人new
    private Singleton(){

    }

    //公共的静态方法，可以直接使用类名调用，返回实例
    //不着急，不是刚声明就初始化，在用的时候才赋值
    public static Singleton getInstance(){
        if(INSTANCE == null){
            INSTANCE = new Singleton();
        }
        return getInstance();
    }
}


```

#### (3)静态内部类实现单例——优雅的懒汉式单例

```java
//其实也是懒汉式
//不获取实例对象的时候是不会new的
package com.ydlclass.singLeton;

public class Singleton2 {

    private Singleton2(){

    }
    //静态内部类
    //静态内部类会在第一次使用的时候加载一次，静态常量会在类加载后初始化，
    private static class SingletonHolder{
        private static final Singleton2 INSTANCE = new Singleton2();
    }
    
    //获取实例对象
    public Singleton2 getSingletonHolder(){
        return SingletonHolder.INSTANCE;
    }
}

```



### 5、匿名内部类

匿名内部类就是没有名字的内部类，可以在定义一个类的时候同时进行初始化。他和局部类很相似，但是没有类名，如果某个局部类只使用一次，那么就可以使用匿名内部类。

#### (1)定义匿名内部类

因为是直接使用的，不存在什么定义不定义的

①、使用接口实现

```JAVA
public class Party{
    
    public static void main(String[] args){
        final int i = 1;
        
        //使用接口实现内部类，Human是一个接口，其中的方法都是抽象方法，使用absoract修饰的，其中的方法都没有方法体，只是返回值类型 方法名(形参列表)
        Party.play(new Human(){
            @OVerride
            public void play(){
			   System.out.println(i);//如果在一个内部类中使用外部的变量，外部的局部变量必须使用final修饰
                System.out.println("妖精is playing")
            }
        });
    }
}

```



### 6、箭头函数

函数式接口，就是一个接口内只有一个方法。

```java
sorterUser.sort(users, (user, other) -> user.getAge() - other.getAge());

```

就是使用`sorterUser.sort(users, new Comparator)`,然后修改返回值，简化，加入`->`就可以了



### 7、值传递和所谓的引用传递—传递都是值拷贝

其实在java中没有引用传递，只有值传递。

```java
public void setAge(int age) {//值传递
        this.age = age;
    }

```

- 定义的时候是形参，调用的时候需要一个实参，age只是一个名字
- 引用传递是形参拷贝的是实参中的引用地址值，所以指向的是同一块空间，所以在方法中修改值，实参指向空间中的值也会改变

> 深入理解

```java
package com.ydlclass.test;

public class Hello {
    public static void stringChange(String str){
        str = "hello";//修改之后方法中的str指向常量池中的hello，并，，没有修改main中的指向
    }

    public static void main(String[] args) {
        String hi = "你好";//hi指向的是常量池，并不是堆中的内存空间
        stringChange(hi);
        System.out.println(hi);
    }
}

```



# 第七章-JVM知识





# 第八章-常用api

今天开始的所有的内容都是api ，常用的、简单的、能够在一天时间归纳出来的一些类，一些api进行介绍

## 一、什么是api

1、概述

API(Application Programming Interface)应用程序接口，是一些预先定义的接口。我们现在理解接口课程很狭隘，因为jdk中本身就有接口的概念。

​		其实我们类的方法，接口的方法在宏观上都能称之为接口。

2、api文档

Tools-Generate JavaDoc-中间输入防止乱码

```java
-encoding utf-8 -charset utf-8

```



## 二、时间相关api

### 1、概述

(1)、时间：需要解释的吗？就是1991年4月8日12点12分40秒，时间会因为时区的不同而不同。

(2)、时区：都学过，都知道东八区吧！

(3)、时间戳：时间戳是指格林威治时间1970年01月01日00时00分00秒(北京时间1970年01月01日08时00分00秒)起至现在的总毫秒数。时间戳在全世界都是固定的。

格林尼治标（英国伦敦郊区的皇家格林尼治天文台的标准时间）准时间的正午是指当太阳横穿格林尼治子午线时（也就是在格林尼治时）的时间。因为本初子午线被定义在通过那里的经线。

```java
Date
getTime
比较时间：before、after

```



```java
//时间戳
System.currentTimeMillis();

```

### 2、Date(日期)类的七天后

> 时间怎么转时间戳
>
> 时间戳怎么转时间

```java
/**
         * 作业：现在的时间加七天是哪天
         */
        //拿到现在的时间
        long time = new Date().getTime();
        //时间戳相加
        time = time + 7*24*60*60*1000;
        //构建新的时间，使用有参数的构建方法
        Date date = new Date(time);
        System.out.println(date);

```

#### 3）常用方法

测试此日期是否在指定日期之后

```
boolean after(Date when)

```

测试此日期是否在指定日期之前

```
boolean before(Date when)

```

获取现在的时间戳

```
getTime()

```



### 3、Calendar(日历)类

```java
Calendar calendar = Calendar.getInstance();
int year = calendar.get(calendar.YEAR);
int month = calendar.get(calendar.MONTH);

```

#### (1)TimeZone(时区)

通过静态方法获取

```java
System.out.println(TimeZone.getDefault());

```

#### (2)ZoneId(区域ID)



#### 4、SimpleDateFormat(日期格式)类

##### (1)format(Date date)方法

将date按照平时使用的格式输出

```java
String format = simpleDateFormat.format(date);

```

(2)applyLocalizedPattern输出格式控制

```java
simpleDateFormat.applyLocalizedPattern("yyyy-MM-dd HH:mm:ss");//年-月-日 HH代表24小时制

```

#### (3)格式化输出现在的时间-工具类展示-可以有很多重载

```java
package com.ydlclass.date;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class DateUtil {
    public static final String DATE_FORMAT = "yyyy年MM月dd日 HH:mm";


    //拿到现在的时间
    public static Date nowDate(){
        return new Date();
    }

    public static Date nowDate(String date){
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat();
        simpleDateFormat.applyLocalizedPattern(DateUtil.DATE_FORMAT);//格式化
        Date str = null;
        try {
            str = simpleDateFormat.parse(date);
        } catch (ParseException e) {
            e.printStackTrace();
        }
        return str;
    }

    public static String nowDateString(){//现在时间格式化输出
        Date date = nowDate();//得到现在的时间
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat();
        simpleDateFormat.applyLocalizedPattern(DateUtil.DATE_FORMAT);//格式化
        String str = simpleDateFormat.format(date);//格式化输出
        return str;
    }
}

```



### 4、jdk8的Instant类-世界标准时间

在时间线上的瞬间点。

自己看java文件：构造器、静态方法、实例方法、成员变量

方法：

1. 参数列表使用什么样的形参，可以是任意的子类
2. 方法是改变具体的值还是返回一个新的值

```java
package com.ydlclass.date;

import java.time.Duration;
import java.time.Instant;
import java.time.ZoneId;
import java.time.ZonedDateTime;
import java.time.temporal.TemporalAmount;

public class InstantTest {
    public static void main(String[] args) {
        Instant now = Instant.now();//获得到的是世界统一的时间
//        now.atZone(ZoneId.of("GMT : +8:00"));
        ZonedDateTime zonedDateTime = now.atZone(ZoneId.of("GMT+08:00"));
        System.out.println(zonedDateTime);
        Instant plus = now.plus(Duration.ofDays(365));//使用接口的时候，使用实现它的哪个类
        System.out.println(plus);
    }
}

```



### 5、localDate(本地时间)类

#### （1）获取当前日期

使用`LocalDate`获取当前日期非常简单，如下所示：

```java
System.out.println("LocalDate.now() = " + LocalDate.now());

LocalDate.now() = 2021-08-11

```

不用任何格式化，输出结果就非常友好，如果使用`Date`，输出这样的格式，还得配合`SimpleDateFormat`指定`yyyy-MM-dd`进行格式化。

#### （2）获取年月日

```java
LocalDate today = LocalDate.now();
System.out.println("today.getYear() = " + today.getYear());
System.out.println("today.getDayOfWeek() = " + today.getDayOfWeek());
System.out.println("today.getMonth() = " + today.getMonth());


today.getYear() = 2021
today.getDayOfWeek() = WEDNESDAY
today.getMonth() = AUGUST

```



```
Month month = today.getMonth();
System.out.println(month.getValue());

```

我们发现Month是一个枚举类，而且LocalDate的月份居然是从1开始的，从此月份的困扰就解决了。

![image-20210811144447836](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC%E4%B8%83%E7%AB%A0-%E5%B8%B8%E7%94%A8api.assets/image-20210811144447836.png)



#### （3）指定日期

```java
LocalDate birthday = LocalDate.of(1991,7, 16);
System.out.println("birthday: " + birthday);

```

> 

如果确定月份，推荐使用另一个重载方法，使用枚举指定月份：

```text
LocalDate specifiedDate = LocalDate.of(1991, Month.JULY, 16);

```

#### （4）比较日期是否相等

```java
LocalDate localDate1 = LocalDate.now();
LocalDate localDate2 = LocalDate.of(1991,7,16);
if (localDate1.equals(localDate2)) {
    System.out.println("localDate1 equals localDate2");
}

```



#### （5）获取日期是本周/本月/本年的第几天

```java
LocalDate today = LocalDate.now();

System.out.println("Today:" + today);
System.out.println("Today is:" + today.getDayOfWeek());
System.out.println("今天是本周的第" + today.getDayOfWeek().getValue() + "天");
System.out.println("今天是本月的第" + today.getDayOfMonth() + "天");
System.out.println("今天是本年的第" + today.getDayOfYear() + "天");

```



#### （6）判断是否为闰年

```java
LocalDate today = LocalDate.now();
System.out.println(today.getYear() + " is leap year:" + today.isLeapYear());

```



### 6、LocalTime

见名知意，上一个是本地日期，而这里是本地时间。

### 7、LocalDateTime

见名知意，自学吧，都一样。



### 8、DateTimeFormatter

JDK8中推出了`java.time.format.DateTimeFormatter`来处理日期格式化问题，《阿里巴巴Java开发手册》中也是建议使用`DateTimeFormatter`代替`SimpleDateFormat`，因为SimpleDateFormate不是线程安全的。

```java
package com.ydlclass.date;

import java.time.*;
import java.time.format.DateTimeFormatter;
import java.time.temporal.TemporalAmount;

public class InstantTest {
    public static void main(String[] args) {
        LocalDateTime now = LocalDateTime.now();
        DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy年MM月dd日");//格式化器
        String format = now.format(dateTimeFormatter);
        /**
         * //格式化之后的文本转成具体的时间，
         * 需要使用LocaDate、LocaDateTime的parse方法，
         * 需要传入我们的格式化器
         */
        LocalDate parse = LocalDate.parse("2022年07月11日", dateTimeFormatter);
        System.out.println(parse);
    }
}

```

9、时间类的转换

(1)instant和date

```java
//Instant转化成Date使用from方法
Instant now = Instant.now();
Date from = Date.from(now); 
System.out.println(from);

```

```java
//Date转成Instant，使用toInstant方法
Instant now = Instant.now();
Date from = Date.from(now);
System.out.println(from);

```

(2)Instant和LocalDateTime

```java
//Instant转LocalDateTime
Instant now = Instant.now();
LocalDateTime localDateTime = LocalDateTime.ofInstant(now, ZoneId.systemDefault());
System.out.println(localDateTime);

```

```java
//LocalDateTime转Instant
LocalDateTime now = LocalDateTime.now();
Instant instant1 = LocalDateTime.now().toInstant(ZoneOffset.UTC);
System.out.println(instant1);

```



(3)Date和LocalDateTime

```java
Date date = new Date();
Instant instant = date.toInstant();
LocalDateTime localDateTimeOfInstant = LocalDateTime.ofInstant(instant, ZoneId.systemDefault());

```

```java
LocalDateTime localDateTime = LocalDateTime.now();
Instant toInstant = localDateTime.atZone(ZoneId.systemDefault()).toInstant();
Date dateFromInstant = Date.from(toInstant);

```



## 三、数学相关api

### 1、Math(数学)类常用方法

```java
System.out.println(Math.floor(2.3));//比实参小的最大整数-向下取整
System.out.println(Math.ceil(2.3));//比实参大的最小整数-向上取整
System.out.println(Math.round(2.55));//四舍五入
System.out.println(Math.random());//随机生成一个0-1的double

```

### 2、BigDecimal(大小数)常用方法

#### (1)核心原理

：十进制小数在计算机的表示中会有误差，把数字扩大，在整数的维度进行计算，并且保留相应的精度信息，然后转成二进制

#### (2)构造器

BigDecimal 有很多重载的构造器，我们几乎可以将任何数字相关的类型转化为一个BigDecimal 对象。

| 构造器                 |                                                              |
| ---------------------- | ------------------------------------------------------------ |
| BigDecimal(int)        | 创建一个具有参数所指定整数值的对象。                         |
| BigDecimal(double)     | 创建一个具有参数所指定双精度值的对象。                       |
| BigDecimal(long)       | 创建一个具有参数所指定长整数值的对象。                       |
| **BigDecimal(String)** | 创建一个具有参数所指定以字符串表示的数值的对象。更适用于计算 |



#### (3)常用方法

BigDecimal提供了大量的计算方法，我们举几个例子

|            |                                                              |                                              |
| ---------- | ------------------------------------------------------------ | -------------------------------------------- |
| BigDecimal | add(BigDecimal)                                              | BigDecimal对象中的值相加，然后返回这个对象。 |
| BigDecimal | subtract(BigDecimal)                                         | BigDecimal对象中的值相减，然后返回这个对象。 |
| BigDecimal | multiply(BigDecimal)                                         | BigDecimal对象中的值相乘，然后返回这个对象。 |
| BigDecimal | divide(BigDecimal)                                           | BigDecimal对象中的值相除，然后返回这个对象。 |
| BigDecimal | **[max](https://www.matools.com/file/manual/jdk_api_1.8_google/java/math/BigDecimal.html#max-java.math.BigDecimal-)**([BigDecimal](https://www.matools.com/file/manual/jdk_api_1.8_google/java/math/BigDecimal.html) val) |                                              |
| BigDecimal | min(BigDecimal val)                                          |                                              |



我们可以从BigDecimal中获取对应的值：

| 返回值 | 方法          | 描述                                 |
| ------ | ------------- | ------------------------------------ |
| double | doubleValue() | 将BigDecimal对象中的值以双精度数返回 |
| float  | floatValue()  | 将BigDecimal对象中的值以单精度数返回 |
| long   | longValue()   | 将BigDecimal对象中的值以长整数返回   |
| int    | intValue()    | 将BigDecimal对象中的值以整数返回     |

#### (4)写的工具类

```java
package com.ydlclass.date;

import java.math.BigDecimal;

public class MathUtil {
    public static double plus(double n1, double n2){
        /**
         * 涉及到类型转换，利用包装类的自动拆装包
         * 就要使用包装类的静态方法进行转化
         */
        BigDecimal bigDecimal = new BigDecimal(Double.toString(n1));//double值变成一个String
        /**
         * 把字符串的“12.3”转化成double小数
         * -举一反三-
         * 使用包装类的静态方法
         */
        double v = Double.parseDouble("12.3");
        BigDecimal add = bigDecimal.add(new BigDecimal(Double.toString(n2)));
        return add.doubleValue();

    }
}


```

### 3、random(随机的)类

#### (1)构造方法

| 方法              | 描述                                       |
| ----------------- | ------------------------------------------ |
| Random()          | 创建一个新的随机数生成器                   |
| Random(long seed) | 使用单个 long 种子创建一个新的随机数生成器 |

#### (2)常用方法

| 方法                         | 描述                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| protected int next(int bits) | 生成下一个伪随机数                                           |
| boolean nextBoolean()        | 返回下一个伪随机数，它是取自此随机数生成器序列的均匀分布的boolean值 |
| void nextBytes(byte[] bytes) | 生成随机字节并将其置于用户提供的 byte 数组中                 |
| double nextDouble()          | 返回下一个伪随机数，它是取自此随机数生成器序列的、在0.0和1.0之间均匀分布的 double值 |
| float nextFloat()            | 返回下一个伪随机数，它是取自此随机数生成器序列的、在0.0和1.0之间均匀分布float值 |
| double nextGaussian()        | 返回下一个伪随机数，它是取自此随机数生成器序列的、呈高斯（“正态”）分布的double值，其平均值是0.0 标准差是1.0 |
| int nextInt()                | 返回下一个伪随机数，它是此随机数生成器的序列中均匀分布的 int 值 |
| int nextInt(int n)           | 返回一个伪随机数，它是取自此随机数生成器序列的、在（包括和指定值（不包括）之间均匀分布的int值 |
| long nextLong()              | 返回下一个伪随机数，它是取自此随机数生成器序列的均匀分布的 long 值。 |

```java
public static void main(String[] args) {
        byte[] bytes = new byte[10];
        Random random = new Random(100);
        random.nextBytes(bytes);
        System.out.println(Arrays.toString(bytes));
    }

```

#### (3)种子介绍

```java
public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Random random = new Random(50);//有种子的时输出
            for (int j = 0; j < 5; j++) {
                System.out.print(" " + random.nextInt(100)+ ",");
            }
            System.out.println();
        }
    }
/*
//数字是根据种子产生的
17, 88, 93, 12, 51,
 17, 88, 93, 12, 51,
 17, 88, 93, 12, 51,
 17, 88, 93, 12, 51,
 17, 88, 93, 12, 51,
*/

```





## 四、工具类

### 1、Arrays工具

#### 常用

```java
public static void main(String[] args) {
        int[] nums = new int[100000];
        Random random = new Random();
        for (int i = 0; i < 100000; i++) {
            nums[i] = random.nextInt();
        }
        long start = System.currentTimeMillis();
        Arrays.sort(nums);
        long end = System.currentTimeMillis();
        System.out.println(end - start);
        start = System.currentTimeMillis();
        Arrays.binarySearch(nums, 234);
        end = System.currentTimeMillis();
        System.out.println(end - start);
    }
equals比较

```

#### 数组拷贝

```java
public static void main(String[] args) {
    int[] ints = {1, 2, 3, 4};
    int[] ints1 = Arrays.copyOf(ints, ints.length * 2);
    System.out.println(Arrays.toString(ints1));
    int[] ints2 = new int[ints.length*2];
    //原数组、从哪里开始、目标数组、从那里拷贝、拷贝长度
    System.arraycopy(ints, 0, ints2, 0, ints.length);
    System.out.println(Arrays.toString(ints2));
}

```



### 2、System获取系统属性

System可以获得很多属性

```java
public static void main(String[] args) {
        System.out.println(System.getProperty("java.version"));//Java版本
        System.out.println(System.getProperty("java.home"));//Java路径
        System.out.println(System.getProperty("os.name"));//操作系统名
        System.out.println(System.getProperty("os.version"));//操作系统版本
        System.out.println(System.getProperty("user.name"));//家文件夹目录
    }

```

### 3、StringBuffer和StringBuilder

可变的字符序列，和String有本质的区别，String是被final修饰的，内容是不能被改变的。

StringBuffer是线程安全的，效率相对低

StringBuilder是线程不安全的，效率相对高

```java
/**
         * 先创建一个空间保存“a”
         * 然后创建一个空间保存"b"
         * 然后又把“a”和“f”加起来保存到一个空间
         * 创建了三个对象
         */
String a = "a";
a = a + "b";

```



#### (1)构造器

| 构造器说明                                                   |
| ------------------------------------------------------------ |
| StringBuilder()                                                       构造一个没有字符的字符串构建器，初始容量为16个字符。 |
| StringBuilder(CharSequence seq)                     构造一个包含与指定的相同字符的字符串构建器 `CharSequence` 。 |
| StringBuilder(int capacity)                                  构造一个没有字符的字符串构建器，由 `capacity`参数指                 定的初始容量 |
| StringBuilder(String str)                                      构造一个初始化为指定字符串内容的字符串构建器。 |

#### (2)常用方法

append()，添加，可以连着使用

insert(int, ...)，指定位置进行添加

sout(StringBuilder)输出的时候也会默认调用toString

```java
public static void main(String[] args) {
        StringBuilder stringBuilder = new StringBuilder("a");
        stringBuilder.append("b").append(1).append("c");
        stringBuilder.insert(2, "xxx");
        System.out.println(stringBuilder);
        System.out.println(stringBuilder.reverse());
        System.out.println(stringBuilder.lastIndexOf("b"));
    }

```





# 第九章 异常处理

## 一、零引发的血案

```java
public static void main(String[] args) {
        while (true){
            int num = 10;
            Scanner scanner = new Scanner(System.in);
            int num1 = scanner.nextInt();
            try{
                int value = num / num1;
                System.out.println(value);
            } catch (Exception e){
                System.out.println("除数不能为0");
            }
        }
    }

```



## 二、异常的继承体系结构

![image-20210715143405204](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%BC%82%E5%B8%B8.assets/image-20210715143405204.png)

- `Throwable` 类是 Java 语言中所有错误或异常的超类。

```java
/**
 * The {@code Throwable} class is the superclass of all errors and
 * exceptions in the Java language. Only objects that are instances of this
 * class (or one of its subclasses) are thrown by the Java Virtual Machine or
 * can be thrown by the Java {@code throw} statement. Similarly, only
 * this class or one of its subclasses can be the argument type in a
 * {@code catch} clause.

```

- Throwable类是所有错误和Java中异常的超类。 只有当对象是此类（或其子类之一）的实例时，才能通过 Java 虚拟机或者 Java throw 语句抛出。 
- Exception和Error都是继承了Throwable类，它是异常处理机制的基本组成类型。
- Exception和Error体现了Java平台设计者对不同异常情况的分类。Exception是程序正常运行中，可以预料的意外情况，可能并且应该被捕获，进行相应处理。
- Error是指在正常情况下，不大可能出现的情况，绝大部分的Error都会导致程序（比如JVM自身）处于非正常的、不可恢复状态。既然是非正常情况，所以不便于也不需要捕获，常见的比如OutOfMemoryError之类，都是Error的子类。





### 1、Error

- Error 是 Throwable 的子类，用于指示合理的应用程序**不应该试图捕获的`严重问题`**。
- Java 程序通常不捕获错误。错误一般发生在严重故障时，它们在Java程序处理的范畴之外。

比如：举个例子，你的程序在运行，内存爆了，你的程序能解决吗？并不能。通常由JVM处理

#### (1)OutOfMemoryError  内存溢出错误

我们为了演示可以直接将堆内存设置成1M

`添加虚拟机参数`：右上角-Edit-Modify options-add VM options

```
-Xms1M -Xmx1M

```

```java
public static void main(String[] args) {
    byte[] bytes = new byte[1024*1024];
}

```

```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
	at com.ydlclass.date.SystemTest.main(SystemTest.java:5)

```



#### (2)StackOverflowError    栈内存溢出错误

```java
public static void main(String[] args) {
    fun();
}

private static void fun(){
    fun();
}

```

```
Exception in thread "main" java.lang.StackOverflowError
	at cn.itnanls.Demo.fun(Demo.java:16)
	at cn.itnanls.Demo.fun(Demo.java:16)

```



#### (3)NoClassDefFoundError      找不到class定义的错误

用notepad++,写两个类：

```java
public class Dog{
	public void eat(){
		System.out.println("I am eating");
	}
}

```

```java
public class Test{
	public static void main(String[] args){
		Dog dog = new Dog();
		dog.eat();
	}
}

```



先编译，Test.java，会出现两个class文件，你把Dog.calss删掉，再执行。就会出现这个错误。

![image-20210715173612840](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%BC%82%E5%B8%B8.assets/image-20210715173612840.png)



这个错误产生的原因大致可以描述如下：

​		要查找的类在编译的时候是存在的，运行的时候却找不到了。这个时候就会导致NoClassDefFoundError。造成该问题的原因可能是打包过程漏掉了部分类，或者jar包出现损坏或者篡改。



### 2、 Exception

**异常**：java语言中，将程序执行中发生的不正常情况称之为异常，就是程序执行的时候出现了你不想看到的情况。

- Exception 异常主要分为两类
  - 一类是 受查异常（检查性异常） ，checkedException。可检查异常在源代码里必须显式地进行捕获处理，这是编译期检查的一部分。Checked Exception的假设是我们捕获了异常，然后恢复程序。但是，其实我们大多数情况下，根本就不可能恢复。这也是为什么有些资料说 Checked Exception 是多余的原因。
  - 一类是 运行时异常（非受查异常），RuntimeException。通常是可以编码避免的逻辑错误，具体根据需要来判断是否需要捕获，并不会在编译期强制要求。



举个例子：你要去机场和你的领导去出差，导致你最后无法坐上飞机的因素有哪些？

1、可以自行解决的：

比如没带身份证，比如起床起晚了。                                          这叫运行时异常，通常是自己导致的。`你可以提前做好准备-自己的逻辑代码出现问题，编译的时候就要解决的-语句之前使用if检查一下`

2、不能自行解决的：

比如在你去的路途中地震了，突然下雨飞机不能起飞				  这叫错误，通常是上帝导致的-`重大错误`

中途堵车了，你领导没来。                                                           这叫检查性异常，通常是别人导致的，你必须提前做好措施-`可以挽回的，提前预判，给出相应的解决方案`

#### （1）常见的检查性异常

| 名字                   | 问题                                               |
| ---------------------- | -------------------------------------------------- |
| IOException            | IO异常，在对流操作时有可能会出现的异常，学流时用到 |
| SQLException           | SQL异常，学数据库时会用到                          |
| ClassNotFoundException | 找不到某个类时，会抛出该异常，反射时会用到         |
| InterruptedException   | 当阻塞方法收到中断请求的时候就会抛出中断异常       |

> ClassNotFoundException

​		Java支持使用Class.forName方法来动态地加载类，任意一个类的类名如果被作为参数传递给这个方法都将导致该类被加载到JVM内存中，如果这个类在类路径中没有被找到，那么此时就会在运行时抛出ClassNotFoundException异常。

```java
Class.forName("com.ydlclass.Dog");//就不存在，不是被删除了

```



> InterruptedException

```java
try {
    Thread.sleep(123);
} catch (InterruptedException e) {
    e.printStackTrace();
}

```

​		如果我们有一个运行中的软件，例如是杀毒软件正在全盘查杀病毒，此时我们不想让它杀毒，这时候点击取消，那么就是正在中断一个运行的线程。

​		其实这段代码的大致意思就是我睡的好好的，有人把我吵醒了。一般是一个程序在睡觉，另一个线程将它打断。



#### （2）常见的非检查性异常：

| 名字                      | 问题                                                         |
| ------------------------- | ------------------------------------------------------------ |
| NullPointerException      | 空指针引用异常，试图调用空对象的方法或者属性时，抛出该异常   |
| ArithmeticException       | 算术运算异常                                                 |
| ClassCastException        | 类型转换异常，`当试图将对象强制转换为不是实例的子类时`，抛出该异常 |
| IndexOutOfBoundsException | 下标越界异常                                                 |
| NumberFormatException     | 数字格式异常                                                 |

解决此类异常通常通过简单的逻辑判断就可以，一般不需要捕获处理：

`空指针异常看是哪行出现的问题，然后deBug，看是谁的引用是空`

`阿里规约规定，字符串比较的时候使用"字符串".equals(字符变量名)，这样就不会因为有人修改变量的引用出现错误`

> NullPointerException

```java
String str = null;
byte[] bytes = str.getBytes();

```

解决方法：

使用if判断，进行debug

```java
String str = null;
if(Objects.nonNull(str)){
	byte[] bytes = str.getBytes();
}

```



> ArithmeticException

```
int i = 0;
int num = 1/i;

```

解决方法：

```java
int i = 0;
if(i != 0){
	int num = 1/i;
}

```



> ClassCastException`当试图将对象强制转换为不是实例的子类时`

```
Animal aniaml = new Dog();
Cat cat = (Cat)animal;

```

解决方法：

```java
Animal aniaml = new Dog();
if(animal instanceof Cat){//进行业务逻辑判断
	Cat cat = (Cat)animal;
}


```



> IndexOutOfBoundsException

```
int[] nums = new int[3];
int i = 3;
nums[i] = 4;

```

解决方法：

```java
int[] nums = new int[3];
int i = 3;
if(i > -1 && i < nums.length){//进行数组下标判断
    nums[i] = 4;
}

```



> NumberFormatException

```java
int num = Integer.parseInt("abc");

```

```java
String str = "abc";
Pattern pattern = Pattern.compile("^[-\\+]?[\\d]*$");
if(pattern.matcher(str).matches()){
    int num = Integer.parseInt(str);
    System.out.println(num);
}

```

#### （3）抛异常

```java
package com.ydlclass;

import java.util.Scanner;

public class Test1 {
    public static void main(String[] args) {
        while (true){
            fun2();//异常一层层的给，最后抛到main
        }
    }

    public static void fun2(){
        try{
            fun();
        } catch(IndexOutOfBoundsException e) {//这里可以是错误的父类，但是不可以是错误的子类

        }
    }

    public static void fun(){
        Scanner scanner = new Scanner(System.in);
        int i = scanner.nextInt();
        if(i > 5){
            System.out.println("继续游戏");
        } else {
            throw new IndexOutOfBoundsException("数组下标越界");
        }
    }
}

```

#### （4）自定义异常

根据不同的业务需求，设计特定的异常，根据捕获的特定的异常，做特定的事，不用RuntimeException的原因是Runtime是超类，不能捕获特定的异常

什么是业务：系统中实现的功能就是业务，要把具体的业务写成具体的代码，`代码是用来服务业务的`

我们遇到不同的问题，我们可以用不同的catch，捕获不同的异常，进行不同的处理

```java
package com.ydlclass.exception;

public class PasswordErrorException extends RuntimeException {
}

```

```java
package com.ydlclass.exception;

public class UserNameErrorException extends RuntimeException{
}

```



```java
{
    public static void main(String[] args) {
        while (true) {
            fun2();
        }
    }

    public static void fun2() {
        try {
            fun();
        } catch (UserNameErrorException e) {
            System.out.println("用户名异常");
        } catch (PasswordErrorException e) {
            System.out.println("密码错误");
        }
    }

    public static void fun() throws UserNameErrorException {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入用户名");
        String str1 = scanner.next();
        if ( !"jing".equals(str1)) {
            throw new UserNameErrorException();//throw不能丢
        }
        System.out.println("请输入密码");
        String mm = scanner.next();
        if ( !"123".equals(mm)) {
            throw new PasswordErrorException();
        }
    }
}

```

（5）StackTrace-栈轨迹-堆栈信息

`排查错误极其重要的信息`

`e.printStackTrace();`

```java
package com.ydlclass.exception;

import java.util.Scanner;

public class Test1 {
    public static void main(String[] args) {
        while (true) {
            fun2();
        }
    }

    public static void fun2() {
        try {
            fun();
        } catch (UserNameErrorException e) {
            System.out.println("用户名异常");
        } catch (PasswordErrorException e) {//下面是抛出异常链
            PasswordErrorException passwordErrorException = new PasswordErrorException(404, "密码error");
            passwordErrorException.initCause(e);
            throw passwordErrorException;
        }
    }

    public static void fun() throws UserNameErrorException {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入用户名");
        String str1 = scanner.next();
        if (!"jing".equals(str1)) {
            throw new UserNameErrorException();
        }
        System.out.println("请输入密码");
        String mm = scanner.next();
        if (!"123".equals(mm)) {
            throw new PasswordErrorException(404, "密码error");//PasswordErrorExcetion添加构建方法
        }
    }
}


```



### 3、throws和throw

throws用在方法名上，就会不报某种异常

throw用在方法内部





### 4、finally关键字

无论有没有异常，都执行finally,不管try、catch是否被调用，finally都会被调用



## 三、try、catch、finally执行顺序

### 面试题一

```java
public static void main(String[] args){
    int result = test1();
    System.out.println(result);
}

public static int test1(){
    int i = 1;
    try{
        i++;
        System.out.println("try block, i = "+i);
    }catch(Exception e){
        i--;
        System.out.println("catch block i = "+i);
    }finally{
        i = 10;
        System.out.println("finally block i = "+i);
    }
    return i;
}

```

输出结果：

```java
try block, i = 2
finally block i = 10
10

```

这算一个相当简单的问题了，没有坑，下面我们稍微改动一下：

```java
public static int test2(){
    int i = 1;
    try{
        i++;
        throw new Exception();
    }catch(Exception e){
        i--;
        System.out.println("catch block i = "+i);
    }finally{
        i = 10;
        System.out.println("finally block i = "+i);
    }
    return i;
}

```

输出结果：

```java
catch block i = 1
finally block i = 10
10

```



### 面试题二

```java
public static void main(String[] args){
    int result = test3();
    System.out.println(result);
}

public static int test3(){
    //try 语句块中有 return 语句时的整体执行顺序
    int i = 1;
    try{
        i++;
        System.out.println("try block, i = "+i);
        return i;
    }catch(Exception e){
        i ++;
        System.out.println("catch block i = "+i);
        return i;
    }finally{
        i = 10;
        System.out.println("finally block i = "+i);
    }
}

```

输出结果：

```java
try block, i = 2
finally block i = 10
2

```

可能有人会所疑惑，原本我们的 i 就被存储在局部变量表 0 位置，而最后 finally 中的代码也的确将 slot 0 位置填充了数值 10，可为什么最后程序依然返回的数值 2 呢？



### 面试题三

//看反编译文件，就会发现catch中的return没了，因为finally肯定会被执行

```java
public static int test4(){
    //finally 语句块中有 return 语句
    int i = 1;
    try{
        i++;
        System.out.println("try block, i = "+i);
        return i;
    }catch(Exception e){
        i++;
        System.out.println("catch block i = "+i);
        return i;
    }finally{
        i++;
        System.out.println("finally block i = "+i);
        return i;
    }
}

```

输出结果：

```java
try block, i = 2
finally block i = 3
3

```





你会发现程序**最终会采用 finally 代码块中的 return 语句进行返回，而直接忽略 try 语句块中的 return 指令**。

- 对于异常的使用有一个不成文的约定：尽量在某个集中的位置进行统一处理，不要到处的使用 try-catch，否则会使得代码结构混乱不堪。
- 按照我们程序员的惯性认知：当遇到return语句的时候，执行函数会立刻返回。但是，在Java语言中，如果存在finally就会有例外。除了return语句，try代码块中的break或continue语句也可能使控制权进入finally代码块。
- 请勿在try代码块中调用return、break或continue语句。万一无法避免，一定要确保finally的存在不会改变方法的返回值。
- **方法返回值有两种类型：值类型与对象引用。对于对象引用，要特别小心，如果在finally代码块中对返回的对象成员属性进行了修改，即使不在finally块中显式调用return语句，这个修改也会作用于返回值上。**



> 我们已经学完了异常知识，最后再给大家几个忠告：

第一，尽量不要捕获类似Exception这样的通用异常，而是应该捕获特定异常。这是因为在日常的开发和合作中，我们读代码的机会往往超过写代码，软件工程是门协作的艺术，所以我们有义务让自己的代码能够直观地体现出尽量多的信息，而泛泛的Exception之类，恰恰隐藏了我们的目的。另外，我们也要保证程序不会捕获到我们不希望捕获的异常。比如，你可能更希望RuntimeException被扩散出来，而不是被捕获。



第二，不要生吞（swallow）异常。这是异常处理中要特别注意的事情，因为很可能会导致非常难以诊断的诡异情况。生吞异常，往往是基于假设这段代码可能不会发生，或者感觉忽略异常是无所谓的，但是千万不要在产品代码做这种假设！如果我们不把异常抛出来，程序可能在后续代码以不可控的方式结束。没人能够轻易判断究竟是哪里抛出了异常，以及是什么原因产生了异常。

# 第十章 泛型Generics、枚举enum

## 泛型

### 一、引出泛型

```java
package com.ydlclass;

/*
引出泛型，类型进行转换
*/
public class Test {
    public static void main(String[] args) {
        SuperArray superArray = new SuperArray();
        superArray.add(new Student("zs", 110));
        superArray.add(new Student("ls", 110));
        superArray.add(new Student("ww", 110));
        superArray.add(new Student("zl", 110));
		superArray.add("111");//类型转换就会出错，我们需要保证，add的时候，添加进去的对象是Student类型的，引出泛型
        for (int i = 0; i <= superArray.size(); i++) {
            if(superArray.lookup(i) instanceof Student){
                Student student = (Student) superArray.lookup(i);
                student.play();
            }
        }

    }
}

```



### 二、泛型的定义

#### 什么是泛型？

​	泛型能够帮助我们把【明确类型】(知道superArray中是什么类型的数据)的工作推迟到创建对象或调用方法的时候。

`superArray包罗万物，但是每次new的时候只能保存一类的对象`

- 封装的时候不明确数据类型
- 创建的时候明确数据类型

#### 1、泛型类

**就是在创建对象的过程中明确数据类型**

泛型类就是把泛型定义在类上，这样在用户使用的时候就可以把类型确定下来

具体的方法就是使用\<>加一个未知数，通常用  T K V 等大写字符表示，事实上只要是个单词就可以。

```java
package com.ydlclass;

public class SuperArray<T> implements CopyUtil {

    private Object[] nums;//只能放Object
    private int currentIndex = -1;
    private int len;

    public SuperArray() {
        this(1);
    }
    public SuperArray(int len) {
        nums = new Object[len];
        this.len = len;
    }
    public Object[] getNums() {
        return nums;
    }
    public void setNums(Object[] nums) {
        this.nums = nums;
    }
    public int getCurrentIndex() {
        return currentIndex;
    }
    public void setCurrentIndex(int currentIndex) {
        this.currentIndex = currentIndex;
    }
    public int getLen() {
        return len;
    }
    public void setLen(int len) {
        this.len = len;
    }
    //增加
    public void add(T date) {
        currentIndex++;
        Object[] temps = new Object[nums.length + 1];
        copy(temps, nums, 0, currentIndex);
        temps[currentIndex] = date;
        nums = temps;
    }
    //指定位置进行增加
    public void addIndex(int index, T date) {
        Object[] temps = new Object[nums.length + 1];
        for (int i = nums.length - 1; i >= index; i--) {
            temps[i] = nums[i - 1];
        }
        this.copy(temps, nums, 0, index - 1);
        temps[index] = date;
        nums = temps;
        currentIndex++;
    }
    //删除
    public void delete(int index) {
        Object[] temps = new Object[nums.length - 1];
        for (int i = currentIndex; i > index; i--) {
            temps[i - 1] = nums[i];
        }
        copy(temps, nums, 0, index - 1);
        nums = temps;
        currentIndex--;
    }
    //查找
    public T lookup(int index){
        return (T)nums[index];
    }
    //改
    public void change(int index, T date){
        nums[index] = date;
    }
    //输出
    public String toString() {
        String str = "[";
        for (int i = 0; i <= currentIndex; i++) {
            str = str + nums[i] + ",";
        }
        return str.substring(0, str.length() - 1) + "]";
    }
    //接口
    @Override
    public void copy(Object[] temps, Object[] nums, int startIndex, int endIndex) {
        for (int i = startIndex; i <= endIndex; i++) {
            temps[i] = nums[i];
        }
    }
}
```

```java
package com.ydlclass;

public class Test {
    public static void main(String[] args) {
        //钻石操作符-自行推断
        //静态类型，动态类型
        SuperArray<Student> superArray = new SuperArray<>();

        superArray.add(new Student("zs", 12));
        superArray.add(new Student("ls", 13));
        superArray.add(new Student("ww", 14));
        superArray.add(new Student("zl", 15));

        for (int i = 0; i <= superArray.size(); i++) {
            Student student = superArray.lookup(i);
            student.play();
        }
    }
}
```



#### 2、泛型方法

在调用方法的时候明确对象类型

可以定义多个，使用`,`隔开

```java
package com.ydlclass;

public class Test2 {
    /**
     *
     * @param t
     * 传入的实参也是泛型的
     * @param <T>
     * 声明一个泛型方法,根据传进来的值进行判断
     * @return
     * 返回值也是泛型
     */
    public <T> T fun(T t){
        System.out.println(t);
        return t;
    }

    public static void main(String[] args) {
        Test2 test2 = new Test2();
        test2.fun(123);
    }
}

```

```java
public <T, K> T fun(T t, K k){
        return t;
}
```

```java
/**
* 有继承、重写、父类引用指向子类对象
*/
/*实现接口的时候明确类型*/
Super<Student> studentSuper = new SuperArray<>();
```

#### 3、泛型的继承

*比较的接口(泛型)*

```java
/**
 * 添加泛型，把具体比较的对象推迟到创建这个类的时候，但是本身是个接口，不能new，
 * 所以确定具体类型的工作只能让子类去完成，父类有泛型，子类可以用明确类型，也可以不明确
 * @param <T>
 */
@FunctionalInterface
public interface Comparator<T> {
    //原来的只能比较User
    //int comparator(User t1, User t2);
    Integer comparator(T t1, T t2);
}

```

```java
//如果改变Comparator接口的类型为Object，实现的时候就这么写
public class StudentComparator implements Comparator{
    @Override
    //方法重写
    public Integer comparator(Object o1, Object o2) {
        if(o1 instanceof Student && o2 instanceof Student){
            return ((Student) o1).getAge() - ((Student) o2).getAge();
        }
        return null;
    }
}

```

```java
/**
 * 在实现的时候就明确类型，最后实现接口<类型>
 */
public class StudentComparator implements Comparator<Student>{
    @Override
    public Integer comparator(Student t1, Student t2) {
        return t1.getAge() - t2.getAge();
    }
}
```

```java
/*
*实例对象被创建的时候才明确类型
*/
//不同的语法有不同的适合场景，Comparator适合在实现的时候就确定类型
package com.ydlclass;

public class Test2 {
    /**
     *
     * @param (T t)
     * 传入的实参也是泛型的
     * @param <T>
     * 声明一个泛型方法,根据传进来的值进行判断
     * @return
     * 返回值也是泛型
     */
    public <T> T fun(T t){
        System.out.println(t);
        return t;
    }

    public static void main(String[] args) {
        /**
         * 前面的是类型操作符，后面的是钻石操作符
         * 父类引用指向子类对象——静态解析的过程中会使用Super的方法，但是在运行的时候动态分派，会具体的使用SuperArray的方法
         * 有继承、重写、父类引用指向子类对象这就是多态
         * 这就是实现接口的时候不确定类型，但是在new对象的时候确定类型
         */
        Super<Student> studentSuper = new SuperArray<>();
    }
}


```

```java
/**
     *这样调用fun方法，就可以使用Super所有的方法了
     * @param super1
     */
    public void fun(Super super1){

    }

```

#### 4、类型通配符

新建三个类：

```java
public class Animal {
}
public class Dog extends Animal {
}
public class Teddy extends Dog {
}

```

​		当我们的一个方法的参数需要传入一个带有参数的类型的时候，可以使用通配符来确定具体传入的对象范围。

```java
public static void print(Comparator<Object> comparator){

}

public static void main(String[] args) {
    Comparator<User> comparator = new Comparator<User>(){
        @Override
        public int compare(User o1, User o2) {
            return o1.getAge() - o2.getAge();
        }
    };
    print(comparator);
}

```

会有以下的报错信息：

![image-20210829092542407](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E6%B3%9B%E5%9E%8B%E6%96%87%E6%A1%A3.assets/image-20210829092542407.png)

意思就是我需要一个泛型是Object的Comparator但你提供的泛型是User，使用通配符就能很好的解决这些问题：

##### （1）无界

类型通配符我感觉上和泛型方法差不多，只是不用在使用前进行定义，例子如下：

```java
public static void main(String[] args) {
    SuperArray<Dog> superArray = new SuperArray<>();
    superArray.add(new Dog());
    superArray.add(new Teddy());
    printSuperArray(superArray);
}

public static void printSuperArray(SuperArray<?> superArray){
    for (int i = 0;i<superArray.size();i++){
        System.out.println(superArray.get(i));
    }
}

```

"?"可以接收任何类型，有些聪明的小伙伴可能发现不加？，连泛型也不要行不行，悄悄的告诉你，可以，但是程序会报一个警告：

```
public static void print(Comparator comparator){  }

```

```
Raw use of parameterized class ‘xxxx‘ 警告
没有类型参数的泛型

```

​		使用原始类型（没有类型参数的泛型）是合法的，但是你永远不应该这样做。如果使用原始类型，就会失去泛型的安全性和表现力。 既然你不应该使用它们，那么为什么语言设计者一开始就允许原始类型呢？答案是：为了兼容性。Java 即将进入第二个十年，泛型被添加进来时，还存在大量不使用泛型的代码。保持所有这些代码合法并与使用泛型的新代码兼容被认为是关键的。将参数化类型的实例传递给设计用于原始类型的方法必须是合法的，反之亦然。

##### （2）上界

​		我们可以使用`(SuperArray<? extends Dog> superArray)`的形式来约定传入参数的上界，意思就是泛型只能是Dog的或者Dog的子类。

```java
  public static void main(String[] args) {
        SuperArray<Animal> superArray = new SuperArray<>();
        superArray.add(new Dog());
        superArray.add(new Teddy());
        superArray.add(new Animal());
        printSuperArray(superArray);
    }
    
    public static void printSuperArray(SuperArray<? extends Dog> superArray){
        for (int i = 0;i<superArray.size();i++){
            System.out.println(superArray.get(i));
        }
    }

```

这种情况下能够接收A类或者A类的子类。

![image-20210716171430366](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E6%B3%9B%E5%9E%8B%E6%96%87%E6%A1%A3.assets/image-20210716171430366.png)

注:当我们使用extends时，我们可以读元素，因为元素都是A类或子类，可以放心的用A类拿出。

##### （3）下界

​		我们可以使用`(SuperArray<? super Dog> superArray)`的形式来约定传入参数的下界，意思就是泛型只能是Dog的或者Dog的超类。

```java
public static void main(String[] args) {
    SuperArray<Teddy> superArray = new SuperArray<>();
    superArray.add(new Teddy());
    printSuperArray(superArray);
}
public static void printSuperArray(SuperArray<? super Dog> superArray){
    for (int i = 0;i<superArray.size();i++){
        System.out.println(superArray.get(i));
    }
}

```

![image-20210716171612067](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E6%B3%9B%E5%9E%8B%E6%96%87%E6%A1%A3.assets/image-20210716171612067.png)

当使用super时，可以添加元素，因为都是A类或父类，那么就可以安全的插入A类。



#### 5、泛型擦除和多态的冲突-反编译、字节码文件看

- JVM会擦除泛型，所以会导致父类的泛型的方法传到子类中是Object类型的参数
- 为了解决泛型擦除，当子类指定类型时，JVM会做一个方法桥接，用Object类型的方法去调用重写的执行类型方法

```java
public class Pair<T> {
    private T value;
    /**
     * 这是一个泛型类，编译后就会类型擦除
     * 类型擦除之后就都是Object类型的
     * 返回值是Object类型的
     * @return
     */
    public T getValue() {
        return value;
    }
    public void setValue(T value) {
        this.value = value;
    }
}

```

```java
package com.ydlclass;

import java.util.Date;

public class DatePair extends Pair<Date>{
    public Date getValue(){
        return super.getValue();
    }
    public void setValue(Date value){
        super.setValue(value);
    }

    public static void main(String[] args) {
        DatePair datePair = new DatePair();
        datePair.setValue(new Date());
    }
}

```

桥接方法：桥接这个类和父类之间的继承和重写的关系

`//ACC_PUBLIC代表的就是桥接方法`

仔细看类型是Object的方法

```java
  Last modified 2022年7月15日; size 977 bytes
  MD5 checksum b5e9763cefcef244b3411e553de4efc0
  Compiled from "DatePair.java"
public class com.ydlclass.DatePair extends com.ydlclass.Pair<java.util.Date>
  minor version: 0
  major version: 55
  flags: (0x0021) ACC_PUBLIC, ACC_SUPER
  this_class: #5                          // com/ydlclass/DatePair
  super_class: #10                        // com/ydlclass/Pair
  interfaces: 0, fields: 0, methods: 6, attributes: 2
Constant pool:
   #1 = Methodref          #10.#35        // com/ydlclass/Pair."<init>":()V
   #2 = Methodref          #10.#36        // com/ydlclass/Pair.getValue:()Ljava/lang/Object;
   #3 = Class              #37            // java/util/Date
   #4 = Methodref          #10.#38        // com/ydlclass/Pair.setValue:(Ljava/lang/Object;)V
   #5 = Class              #39            // com/ydlclass/DatePair
   #6 = Methodref          #5.#35         // com/ydlclass/DatePair."<init>":()V
   #7 = Methodref          #3.#35         // java/util/Date."<init>":()V
   #8 = Methodref          #5.#40         // com/ydlclass/DatePair.setValue:(Ljava/util/Date;)V
   #9 = Methodref          #5.#41         // com/ydlclass/DatePair.getValue:()Ljava/util/Date;
  #10 = Class              #42            // com/ydlclass/Pair
  #11 = Utf8               <init>
  #12 = Utf8               ()V
  #13 = Utf8               Code
  #14 = Utf8               LineNumberTable
  #15 = Utf8               LocalVariableTable
  #16 = Utf8               this
  #17 = Utf8               Lcom/ydlclass/DatePair;
  #18 = Utf8               getValue
  #19 = Utf8               ()Ljava/util/Date;
  #20 = Utf8               setValue
  #21 = Utf8               (Ljava/util/Date;)V
  #22 = Utf8               value
  #23 = Utf8               Ljava/util/Date;
  #24 = Utf8               main
  #25 = Utf8               ([Ljava/lang/String;)V
  #26 = Utf8               args
  #27 = Utf8               [Ljava/lang/String;
  #28 = Utf8               datePair
  #29 = Utf8               (Ljava/lang/Object;)V
  #30 = Utf8               ()Ljava/lang/Object;
  #31 = Utf8               Signature
  #32 = Utf8               Lcom/ydlclass/Pair<Ljava/util/Date;>;
  #33 = Utf8               SourceFile
  #34 = Utf8               DatePair.java
  #35 = NameAndType        #11:#12        // "<init>":()V
  #36 = NameAndType        #18:#30        // getValue:()Ljava/lang/Object;
  #37 = Utf8               java/util/Date
  #38 = NameAndType        #20:#29        // setValue:(Ljava/lang/Object;)V
  #39 = Utf8               com/ydlclass/DatePair
  #40 = NameAndType        #20:#21        // setValue:(Ljava/util/Date;)V
  #41 = NameAndType        #18:#19        // getValue:()Ljava/util/Date;
  #42 = Utf8               com/ydlclass/Pair
{
  public com.ydlclass.DatePair();
    descriptor: ()V
    flags: (0x0001) ACC_PUBLIC
    Code:
      stack=1, locals=1, args_size=1
         0: aload_0
         1: invokespecial #1                  // Method com/ydlclass/Pair."<init>":()V
         4: return
      LineNumberTable:
        line 5: 0
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       5     0  this   Lcom/ydlclass/DatePair;

  public java.util.Date getValue();//Date的getValue
    descriptor: ()Ljava/util/Date;
    flags: (0x0001) ACC_PUBLIC
    Code:
      stack=1, locals=1, args_size=1
         0: aload_0
         1: invokespecial #2                  // Method com/ydlclass/Pair.getValue:()Ljava/lang/Object;
         4: checkcast     #3                  // class java/util/Date
         7: areturn
      LineNumberTable:
        line 7: 0
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       8     0  this   Lcom/ydlclass/DatePair;

  public void setValue(java.util.Date);//Date的setValue
    descriptor: (Ljava/util/Date;)V
    flags: (0x0001) ACC_PUBLIC
    Code:
      stack=2, locals=2, args_size=2
         0: aload_0
         1: aload_1
         2: invokespecial #4                  // Method com/ydlclass/Pair.setValue:(Ljava/lang/Object;)V
         5: return
      LineNumberTable:
        line 10: 0
        line 11: 5
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       6     0  this   Lcom/ydlclass/DatePair;
            0       6     1 value   Ljava/util/Date;

  public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: (0x0009) ACC_PUBLIC, ACC_STATIC
    Code:
      stack=3, locals=2, args_size=1
         0: new           #5                  // class com/ydlclass/DatePair
         3: dup
         4: invokespecial #6                  // Method "<init>":()V
         7: astore_1
         8: aload_1
         9: new           #3                  // class java/util/Date
        12: dup
        13: invokespecial #7                  // Method java/util/Date."<init>":()V
        16: invokevirtual #8                  // Method setValue:(Ljava/util/Date;)V
        19: return
      LineNumberTable:
        line 14: 0
        line 15: 8
        line 16: 19
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0      20     0  args   [Ljava/lang/String;
            8      12     1 datePair   Lcom/ydlclass/DatePair;

  public void setValue(java.lang.Object);//Object的setValue
    descriptor: (Ljava/lang/Object;)V//代表是一个引用数据类型   //ACC_PUBLIC代表的就是桥接方法
    flags: (0x1041) ACC_PUBLIC, ACC_BRIDGE, ACC_SYNTHETIC
    Code:
      stack=2, locals=2, args_size=2
         0: aload_0
         1: aload_1
         2: checkcast     #3                  // class java/util/Date
         5: invokevirtual #8                  // Method setValue:(Ljava/util/Date;)V //调用了这个方法，桥接方法，JVM利用这种桥接方法形成的方法重写
         8: return
      LineNumberTable:
        line 5: 0
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       9     0  this   Lcom/ydlclass/DatePair;

  public java.lang.Object getValue();
    descriptor: ()Ljava/lang/Object;
    flags: (0x1041) ACC_PUBLIC, ACC_BRIDGE, ACC_SYNTHETIC
    Code:
      stack=1, locals=1, args_size=1
         0: aload_0
         1: invokevirtual #9                  // Method getValue:()Ljava/util/Date;
         4: areturn
      LineNumberTable:
        line 5: 0
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       5     0  this   Lcom/ydlclass/DatePair;
}
Signature: #32                          // Lcom/ydlclass/Pair<Ljava/util/Date;>;
SourceFile: "DatePair.java"

```



#### 6、静态和泛型

泛型类中的静态方法和静态变量不可以使用泛型类所声明的泛型类型参数

举例说明：

```java
public class Test2<T> {    
    public static T one;   //编译错误    
    public static T show(T one){ //编译错误    
        return null;    
    }    
}

```

​		因为泛型类中的泛型参数的实例化是在定义对象的时候指定的，而静态变量和静态方法不需要使用对象来调用。对象都没有创建，如何确定这个泛型参数是何种类型，所以当然是错误的。

但是要注意区分下面的一种情况：

```java
public class Test2<T> {    

    public static <T> T show(T one){ //这是正确的    
        return null;    
    }    
}

```

因为这是一个泛型方法，在泛型方法中使用的T是自己在方法中定义的 T，而不是泛型类中的T。

- 静态变量不可以
- 静态方法的形参直接写也不可以
- 但是可以写静态泛型方法



## 枚举

### 一、引出枚举

固定且有限的、一定数量的数组可以表示的可以使用静态常量

> 简单的保存信息-使用静态常量

```java
public class SeasonConstant {
    public static final int SPRING = 1;
    public static final int SUMMER = 2;
    public static final int AUTUMN = 3;
    public static final int WINTER = 4;
}

```

> 保存更多的信息-使用单例实现

```java
package com.ydlclass;

public class Season {
    private int value;
    private String name;
	//定义四个静态常量，内存中独此一份
    public static final Season SPRING = new Season(1, "春天");
    public static final Season SUMMER = new Season(2, "夏天");
    public static final Season AUTUMN = new Season(3, "秋天");
    public static final Season WINTER = new Season(4, "冬天");

    public Season() {
    }
    public Season(int i, String str) {
    }
    public int getValue() {
        return value;
    }
    public void setValue(int value) {
        this.value = value;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}

```

> 使用枚举

`上面两种方法重复代码过多`

```java
public enum SeasonEnum {
    //这就是四个对象，new了四个Season
    //每个枚举都相当于构建了一个静态常量
    SPRING, SUMMER, AUTUMN, WINTER;
}

```



### 二、枚举方法

#### 1、常用方法

| 方法                          | 说明                                   |
| ----------------------------- | -------------------------------------- |
| values()     静态的自动生成的 | 可以遍历enum实例，其返回enum实例的数组 |
| ordinal()   父类的实例方法    | 返回每个实例在声明时的次序             |
| name()      父类的实例方法    | 返回enum实例声明时的名称               |
| getDeclaringClass()           | 返回其所属的enum类                     |
| valueOf()    静态的自动生成的 | 根据给定的名称返回相应的enum实例       |

```java
public static void main(String[] args) {
        //因为SPRING也是对象，所以可以使用实例方法
        System.out.println(SeasonEnum.SPRING.ordinal());

        //使用静态方法，SeasonEnum没有的去父类找
        //values()是编译过程中自动生成的
        //具体的看字节码文件
        SeasonEnum[] values = SeasonEnum.values();//拿到所有的枚举项
        for (int i = 0; i < values.length; i++) {
            System.out.println(values[i]);
        }
        //根据具体的名字得到具体的枚举项
        SeasonEnum spring = SeasonEnum.valueOf("SPRING");
        System.out.println(spring);
    }

```



#### 2、添加新方法

```java
public enum SeasonEnum {
    //这就是四个对象，new了四个Season
    SPRING("春天","万物复苏"),
    SUMMER("夏天","热死"),
    AUTUMN("秋天", "收获的季节"),
    WINTER;

    private String name;//名字
    private String detail;//描述
}

```

```java
public static void test(SeasonEnum seasonEnum){
        switch(seasonEnum){
            case SPRING:
                System.out.println("春天了");break;
            case SUMMER:
                System.out.println("夏天了");break;
            case AUTUMN:
                System.out.println("秋天了");break;
            case WINTER:
                System.out.println("冬天了");break;
        }
    }

```



### 三、静态导包

```java
import static com.ydlclass.SeasonEnum.*;

```

- 注意只能导入一个
- 就这样可以导入一个枚举的所以有静态对象



### 四、枚举实现单例-懒汉式

> 因为JVM保证枚举实例都是单例

```java
package com.ydlclass;

public class Singleton {

    //第一步：私有化构造器
    private Singleton(){

    }
    //第二步：公开的方法获得枚举单例
    //不调用这个方法就不会调用内部类，就不会创建枚举对象 
    public static Singleton getInstance(){
        return SingletonHolder.INSTANT.singleton;
    }

    //第三步：定义枚举内部类,单例持有者
    private enum SingletonHolder{
        INSTANT;//这个是SingletonHolder的对象  //这个枚举会在类加载的时候进行初始化，然后就会调用构造器，
        private Singleton singleton;//添加一个属性Singleton，让他持有一个Singleton对象
        SingletonHolder(){
            this.singleton = new Singleton();
        }
    }
}


```



# 第十一章 多线程

![image-20210831100614397](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831100614397.png)

## 一、进程和线程

### 1、进程

- 进程更强调的是资源分配
- 进程是程序的一次执行过程，它有自己独立的生命周期，在启动程序的时候产生，运行程序时存在，关闭程序时消亡

最原始的计算机就是单进程的，同一时间只能执行一个进程，我们可以把现在的【计算器】当做最原始的计算机，同一时间只能执行一段代码。比如我们要计算一个账本的总账，只能一个数字一个数字的相加，而且，在这其中你还不能做其他的事情。

但是随着计算机的发展，计算任务的不断提升，单个进程的方式人们就很难接受了，与此同时cpu的计算能力也大幅提升，于是就产生了按照`时间线交替执行`不同进程的方式。	两个进程交替执行，每个执行一点点时间，在感觉上就像同时执行两个进程了。

![image-20210831102730062](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831102730062.png)当然，我们还会有疑问？

如果一个进程有多个任务怎么办，比如我们使用浏览器同时下载八个小电影，一种方式是一个一个下载，一个完了下一个开始，另一种方式就是同时开始，最后一个下载完成结束。

第一种就是我们的串行执行，没什么好说的，第二种就需要其他的解决方案了，给每一个下载任务分配一个进程可以吗？每一个进程会分配独立的内存资源，原则上是可以的。

![image-20210831104120749](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831104120749.png)

如果为每一个任务分配单独的进程去执行，进程间的通信就会不可避免，比如某一个下载任务完成了肯定要通知浏览器啊，这样就会产生一个问题，微信的进程是不是能访问QQ的进程？`病毒`是不是就很容易操作你运行中的进程，修改你的数据了。所以，在计算机的设计当中就引入了线程的概念



### 2、线程-时间片实现

进程强调`内存资源分配`，线程强调`计算资源分配`，有了线程的概念，一个进程的线程就不能修改另一个线程的数据，隔离性更好，安全性更好。



![image-20210831105047385](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831105047385.png)

一个进程跑起来就会有一个主线程，一个线程中做好几件事情就会分配几个新的线程，但是线程的数量是有限的，

### 3、上下文切换——数据就是上下文

![image-20210831112740243](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831112740243.png)

> 两个问题——多线程带来的性能开销的最大问题

- 谁来调度线程——系统内核
  - 用户线程切换的时候需要先切换到内核调度总线程中，用户态<——>内核态`切换`
- 时间片的执行是怎么衔接上的——上下文保存
  - 线程挂起的时候保存数据，恢复线程的时候需要恢复数据

线程的每次切换都需要进行用户态到内核态的来回切换，同时伴随着上下文的切换，是一个比较消耗资源的操作，所以一个计算机当中不是线程越多越好，线程如果太多也是有可能拖垮整个系统的。



### 4、创建线程的方法

#### (1)继承Thread重写run()方法

```java
public class UseThread extends Thread{
    @Override
    public void run() {
        System.out.println(2);
    }
    
    /**
     *start才是启动线程的方式
     * 启动线程消耗的资源比较多，所以显示的就会滞后
     * 可以先让主线程睡10ms
     */
    public static void main(String[] args) throws InterruptedException {
        System.out.println(1);
        new UseThread().start();
        sleep(10);
        System.out.println(3);
    }
}

```

#### (2)实现Runnable接口，并且实现run()方法

<1>实现接口

```java
public class UseRunnable implements Runnable{
    @Override
    public void run() {
        System.out.println(2);
    }

    /**
     *Runnable是一个函数式接口，没有start方法
     * new一个Thread，然后传入实现Runnable的实例
     * 使用的是Thread的有参构造
     */
    public static void main(String[] args) {
        System.out.println(1);
        new Thread(new UseRunnable()).start();
        System.out.println(3);
    }
}

```

<2>匿名内部类—箭头函数

```java
public static void main(String[] args) {
        System.out.println(1);
        new Thread(() -> System.out.println(4)).start();
        System.out.println(3);
    }
}

```

#### (3)使用Lammbda表达式



#### (4)有返回值的线程

```java
/**
 * Callable是一个泛型接口
 */
public class UseCallable implements Callable<Integer> {

    @Override
    public Integer call() throws Exception {
        Thread.sleep(3000);
        return 2;
    }

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        //FutureTask就是为了保存一个将来的返回值
        //FutureTask实现RunnableFuture接口，RunnableFuture实现Runnable接口
        FutureTask<Integer> futureTask = new FutureTask<>(new UseCallable());//未来的任务
        //new Thread()需要Runnable的对象，FutureTask就是一个Runnable
        new Thread(futureTask).start();
        //阻塞的get方法，等待线程的返回值——阻塞的是main的线程，等待integer拿到返回值才继续进行
        Integer integer = futureTask.get();
        System.out.println(integer);
    }
}

```

```java
public class UseCallableTwo implements Callable<Integer> {

    @Override
    public Integer call() throws Exception {
        Thread.sleep(3000);
        return 1;
    }

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        System.out.println(2);
        FutureTask<Integer> futureTask = new FutureTask<>(new UseCallable());
        System.out.println(3);
        new Thread(futureTask).start();
        System.out.println(4);
        //主线程卡住，等待返回值
        int result = futureTask.get();
        System.out.println(5);
        System.out.println(result);
        System.out.println(6);
    }
}

```

线程的好处：

- 加速，提高cpu的使用率
- 异步的无干扰的进行其他业务的操作

### 5、守护线程

Java提供两种类型的线程：`用户线程`和`守护程序线程`。守护线程旨在为用户线程提供服务，并且仅在用户线程运行时才需要。

> 守护线程的使用

​		守护线程对于后台支持任务非常有用，例如垃圾收集，释放未使用对象的内存以及从缓存中删除不需要的条目。大多数JVM线程都是守护线程。在比如qq等等聊天软件,主程序是非守护线程,而所有的聊天窗口是守护线程,当在聊天的过程中,直接关闭聊天应用程序时,聊天窗口也会随之关。包括word中我们在书写文字的时候，还有线程帮我们进行拼写检查，这都是守护线程。

```java
public class Deamon {

    public static void main(String[] args) {
        Thread t1 = new Thread(() -> {
            int count = 10;
            Thread t2 = new Thread(() -> {
                while (true){
                    ThreadUtils.sleep(300);
                    System.out.println("我是个守护线程！");
                }
            });
            t2.setDaemon(true);
            t2.start();

            while (count >= 0){
                ThreadUtils.sleep(200);
                System.out.println("我是用户线程！");
                count--;
            }
            System.out.println("用户线程结束-------------------");
        });
        t1.setDaemon(true);//可以把两个守护线程都注释掉，看输出
        t1.start();
    }

}

```



### 6、线程的生命周期

```java
public enum State {
        /**
         * Thread state for a thread which has not yet started.
         */
        NEW,

        /**
         * Thread state for a runnable thread.  A thread in the runnable
         * state is executing in the Java virtual machine but it may
         * be waiting for other resources from the operating system
         * such as processor.
         */
        RUNNABLE,

        BLOCKED,

        WAITING,

        TIMED_WAITING,

        TERMINATED;
    }

```

| 状态                          | 弹幕     | 描述                                                         |
| ----------------------------- | -------- | ------------------------------------------------------------ |
| 【NEW】                       | 出生状态 | 这个状态主要是线程未被Thread.start()调用前的状态。           |
| 【RUNNABLE】                  | 就绪状态 | 线程正在JVM中被执行，等待来自操作系统(如处理器)的调度。      |
| 【BLOCKED】被动的等待，堵车   | 阻塞状态 | 阻塞，因为某些原因不能立即执行需要挂起等待。                 |
| 【WAITING】不知道还要多久过来 | 持续等待 | 无限期等待，由于线程调用了`Object.wait(0)`，`Thread.join(0)`和`LockSupport.park`其中的一个方法，线程处于等待状态，其中调用`wait`, `join`方法时未设置超时时间。 |
| 【TIMED_WAITING】等你半个小时 | 超时等待 | 有限期等待， 线程等待一个指定的时间，比如线程调用了`Object.wait(long)`, `Thread.join(long)`,`LockSupport.parkNanos`, `LockSupport.parkUntil`方法之后，线程的状态就会变成TIMED_WAITING |
| 【TERMINATED】                | 线程终止 | 终止的线程状态，线程已经完成执行。                           |

![image-20210830182953008](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210830182953008.png)

- 等待需要打断
- 阻塞、等待之后都要重新进入就绪状态，等待系统调用

#### //代码

```java
public class TestJoin {
    /**
     * 主线程创建两个线程，启动线程，主线程输出
     * @param args
     */
    public static void main(String[] args) {
        Thread t1 = new Thread(() -> {
            ThreadUtils.sleep(2000);
            System.out.println("t1————————————————————");
        });
        Thread t2 = new Thread(() -> {
            ThreadUtils.sleep(3000);
            System.out.println("t2_____________________");
        });
        t1.start();
        t2.start();

        try {
            t1.join();//哪个线程创建的t1、哪个调用的t1就阻塞哪个
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("main————————————");
        /**
         * 运行顺序是，创建两个线程，启动线程，尝试执行t1，然后输出main，最后执行t2
         */
    }
}

```



## 二、线程安全的讨论

### 1、cpu多核缓存架构

![image-20210831125522665](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831125522665.png)

> CPU分为三级缓存： 每个CPU都有L1,L2缓存，但是L3缓存是多核公用的。

> CPU查找数据的顺序为： CPU -> L1 -> L2 -> L3 -> 内存 -> 硬盘

| 从CPU到  | 大约需要的时间 |
| -------- | -------------- |
| 主存     | 60~80纳秒      |
| L3 cache | 大约15纳秒     |
| L2 cache | 大约3纳秒      |
| L1 cache | 大约1纳秒      |
| 寄存器   | 大约0.3纳秒    |

> 局部性原理
>
> 进一步优化，CPU每次读取一个数据，并不是仅仅读取这个数据本身，而是会读取与它相邻的`64个字节`的数据，称之为【缓存行】，因为CPU认为，我使用了这个变量，很快就会使用与它相邻的数据，这是计算机的局部性原理。这样，就不需要每次都从主存中读取数据了。

这个其实很好理解：

```java
public static void main(String[] args) {
    int nums[] = new int[10];
    for (int i = 0; i < nums.length; i++) {
        System.out.println(nums[i]);
    }
}

```

​		比如说这个代码，CPU读到nums[0]这后大概率就会读nums[1]，这就是`局部性原理`的体现，当然一个缓存行现在是64个字节，这是很多科学家调优的结果，如果设计的太小则难以`命中`，如果设计的大了则读取比较慢，这是目前的最优解。



这种多级缓存的结构下，会有什么`问题`呢？最经典的就是`【可见性的问题】`，可以简单的理解为，一个线程修改的值对其他线程可能不可见。

​		比如两个CPU读取了一个缓存行，缓存行里有两个变量，一个x一个y。第一颗CPU修改了x的数据，还没有刷回主存，此时第二颗CPU，从主存中读取了未修改的缓存行，而此时第一颗CPU修改的数据刷回主存，这时就出现，第二颗CPU读取的数据和主存不一致的情况。

​		为了解决数据不一致的问题，很多厂商提出了自己的解决方案，比如英特尔的MESI协议。

```
MESI协议规定每条缓存都有一个状态位，同时定义了一下四种状态：
修改态 (Modified) 此缓存被修改过，内容与住内存不同，为此缓存专有
专有态 (Exclusive) 此缓存与主内存一致，但是其他CPU中没有
共享态 (Shared) 此缓存与住内存一致，但也出现在其他缓存中。
无效态 (Invalid) 此缓存无效，需要从主内存中重新读取。

```

​		除了存在可见性的问题，当多个线程同时修改相同资源的时候，还会存在资源的争夺问题。

![image-20210831142945158](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831142945158.png)

我们在执行这一段代码之后，有可能最后的结果是2。



​		除了增加高速缓存之外，为了使处理器内部的运算单元尽量被充分利用。处理器可能会对输入的代码进行【乱序执行】，优化处理器会在计算之后将乱序执行的结果【进行重组】，保证该结果与顺序执行的结果是一致的，但并不保证程序中各个语句的先后执行顺序与输入代码中的顺序一致。因此如果存在一个计算任务，依赖于另外一个依赖任务的中间，结果那么顺序性不能靠代码的先后顺序来保证。 Java虚拟机的即时编译器中也有【指令重排】的优化。

​		咱们可以举一个简单的例子来形象的说明一下，比如现在我们有这么一个需求，有四条指令，这四条指令分别是让四个人在四张纸上写下【新年快乐】四个字。但是在这个过程当中，有的人写的快，有的人写得慢，而如果我们非要按照新年快乐这四个顺序去执行这个工作的话，可能时间会浪费的多一点，那我们不妨让这四个人分别去写他们这四个字儿，我们等着这四个人最后一个写完了，然后再把这四个字组合在一起，我们就达到目的了，这样的乱序执行效率可能会更高一些。

//乱序执行的结果和顺序执行的结果是一样的



### 2、JMM-java内存模型

强调在高并发、多线程的情况下，我们的线程是怎么利用内存的

![image-20210831125228377](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831125228377.png)

每个线程都有自己的工作内存，然后工作内存访问主内存，剩下的交给计算机

- 可见性的问题

### 3、JMM模型中存在的问题

- 在执行过程中，为了提高性能，编译器和处理器常常会对指令做重排序。

#### (1)指令重排

```java
public class OutOfOrderExecution {
    private static int x = 0, y = 0;
    private static int a = 0, b = 0;
    private static int count = 0;

    private static volatile int NUM = 0;

    public static void main(String[] args)
            throws InterruptedException {
        long start = System.currentTimeMillis();
        for (;;) {
            Thread t1 = new Thread(new Runnable() {
                @Override
                public void run() {
                    a = 1;
                    x = b;
                }
            });
            Thread t2 = new Thread(new Runnable() {
                @Override
                public void run() {
                    b = 1;
                    y = a;
                }
            });
            t1.start();
            t2.start();
            t1.join();
            t2.join();
            System.out.println("一共执行了：" + (count++) + "次");
            if(x==0 && y==0){
                long end = System.currentTimeMillis();
                System.out.println("耗时：+"+ (end-start) +"毫秒，(" + x + "," + y + ")");
                break;
            }
            a=0;b=0;x=0;y=0;
        }
    }
}

```

##### 半初始化相关知识

一个对象初始化的状态：，如果不想被乱序执行就使用volatile关键字进行修饰

`Dog dog = new Dog();`

1. new一个对象—堆内存分配空间
2. 调用构造器
3. 栈空间进行引用

对象的半初始化状态就是上面的三个步骤没有被执行完，中间插入一条指令，使用了这个对象，就会出现异常。



#### (2)可见性

```java
package com.ydlclass;

public class Test {
    public static boolean flag = false;
    public static void main(String[] args) {
        new Thread(()->{
            while(!flag){}//会从缓冲区中拿flag
            System.out.println("你能看见我吗");
        }).start();

        ThreadUtils.sleep(2000);
        flag = true;//即使已经修改，while还是看不见，这就是可见性的问题，使用volatile关键字可以解决
    }
}


```

`public volatile static boolean flag = false;`

写操作是：立刻强制刷在主存，并且将其他缓存区域的值设置为不可用，直接从主存中拿

volatile能够强制对改变量的读写直接在主存中进行，从而解决了不可见的问题

##### volatile的作用

1. 禁止指令重排
2. 内存的可见性

> happens-before语义

​		 JMM用【happens-before】的概念来阐述操作之间的内存可见性。在JMM中，如果一个操作执行的结果需要对另一个操作可见，那么这两个操作之间必须要存在happens-before关系 。

​		在Java 规范提案中为让大家理解内存可见性的这个概念，提出了happens-before的概念来阐述操作之间的内存可见性。对应Java程序员来说，理解happens-before是理解JMM的关键。JMM这么做的原因是：程序员对于这两个操作是否真的被重排序并不关心，程序员关心的是程序执行时的语义不能被改变（即`执行结果不能被改变`）。因此，happens-before关系本质上和as-if-serial语义是一回事。`as-if-serial语义保证单线程内程序的执行结果不被改变，happens-before关系保证正确同步的多线程程序的执行结果不被改变`。

#### (3)线程争抢

```java
public class Test {
    private static int COUNT = 0;
    public static void add(){
        COUNT++;
    }
    public static void main(String[] args) throws InterruptedException {
        Thread t1 = new Thread(()->{
            for (int i = 0; i < 10000; i++) {
                add();
            }
        });
        Thread t2 = new Thread(()-> {
            for (int i = 0; i < 10000; i++) {
                add();
            }
        });
        t1.start();
        t2.start();
        t1.join();
        t2.join();
        System.out.println(COUNT);
    }

```

多个线程调用共同资源，修改共享资源的时候就会出现线程争抢，线程争抢会出现数据安全问题

使用JMM内存图进行分析

```java
public class Test {
    private  static volatile int COUNT = 0;
    public synchronized static void add(){//方法使用syn修饰
        COUNT++;
    }
    public static void main(String[] args) throws InterruptedException {
        Thread t1 = new Thread(()->{
            for (int i = 0; i < 10000; i++) {
                add();
            }
        });
        Thread t2 = new Thread(()-> {
            for (int i = 0; i < 10000; i++) {
                add();
            }
        });
        t1.start();
        t2.start();
        t1.join();
        t2.join();
        System.out.println(COUNT);
    }

```

```java
package com.ydlclass;

public class Ticked implements Runnable {
    private static int COUNT = 100;
    String name;

    public Ticked() {
    }

    public Ticked(String name) {
        this.name = name;
    }


    @Override
    public void run() {
        while (COUNT > 0){
            ThreadUtils.sleep(100);
            synchronized (jTicked.class){//锁住代码
                System.out.println(name + "出票一张， 还有" + Ticked.COUNT-- +"张");
            }
        }
    }

    public static void main(String[] args) {
        Thread t1 = new Thread(new Ticked("一号窗口"));
        Thread t2 = new Thread(new Ticked("二号窗口"));
        t1.start();
        t2.start();
    }
}


```

### 4、线程安全的实现方法

#### (1)数据不可变

在Java中，一切不可变的(immutable)一定是线程安全的，无论是对象的方法实现还是方法的调用者，都不需要再进行任何线程安全的措施，比如final关键字修饰的基础数据类型，再比如说Java字符串，只要一个不可变的对象被正确的构建出来，那外部的可见状态永远不会改变，永远都不会看见他在多个线程中处于不一致的状态，带来的安全性是最直接最纯粹的。

#### (2)互斥同步(悲观的并发策略)

#### (3)非阻塞同步(自旋)

线程较少使用自旋，不用挂起线程

阻塞和唤醒都会造成内核态到用户态的切换，都会有上下文的切换

#### (4)无同步方案

```java
package com.ydlclass;

public class Test {
    static final ThreadLocal<Integer> threadLocal = new ThreadLocal<>();
    /**
     * 这个number要用
     * 我们使用number的时候，number的值会不会改变如果我们改变number的值，会不会改变主存中的number
     */
    private static int number = 0;

    public static void main(String[] args) throws InterruptedException {
        Thread t1 = new Thread(new Runnable() {
            @Override
            public void run() {
                threadLocal.set(number);//将number的值拷贝到线程内存空间中
                for (int i = 0; i < 1000; i++) {//在自己的线程内存中进行变量的操作
                    threadLocal.set(threadLocal.get() + 1);//设置threadLocal的值为threadLocal+1
                    System.out.println("t1------: " + threadLocal.get());
                }
            }
        });
        Thread t2 = new Thread(new Runnable() {
            @Override
            public void run() {
                threadLocal.set(number);
                for (int i = 0; i < 1000; i++) {
                    threadLocal.set(threadLocal.get() + 1);
                    System.out.println("t2------: " + threadLocal.get());
                }
            }
        });
        t1.start();
        t1.join();
        t2.start();
    }
}


```



## 三、锁机制--7.20

### 1、synchronized(内置锁、隐式锁)简介

就是一把锁，给了方法，线程在执行方法的时候会先获得锁，把锁锁上

JVM会在执行的时候把class文件和字节码文件生成一个`class对象`，全内存只有一份，也是一个对象，锁在实例方法上相当于锁的对象，锁在静态方法上相当于锁的类

> synchronized 有三种方式来加锁，分别是

1. 修饰实例方法，作用于当前实例加锁，进入同步代码前要获得当前实例的锁
2. 静态方法，作用于当前类对象加锁，进入同步代码前要获得当前类对象的锁
3. 修饰代码块，指定加锁对象，对给定对象加锁，进入同步代码库前要获得给定对象的锁。

> 使用方法：

| 分类   | 具体分类       | 被锁对象             | 伪代码                                              |
| ------ | -------------- | -------------------- | --------------------------------------------------- |
| 方法   | 实例方法       | 调用该方法的实例对象 | public synchronized void method(){  }               |
| 方法   | 静态方法       | 类对象Class对象      | public static synchronized void method(){  }        |
| 代码块 | this           | 调用该方法的实例对象 | synchronized(this){  }                              |
| 代码块 | 类对象         | 类对象               | synchronized(Demo.class){  }                        |
| 代码块 | 任意的实例对象 | 创建的任意对象       | Object lock= new Object();   synchronized(lock){  } |

#### 1、静态方法锁

```java
public synchronized static void say2() {
        ThreadUtils.sleep(100);
        System.out.println("say2");
    }

public static void main(String[] args) {
        Test test = new Test();
        for (int i = 0; i < 50; i++) {
            new Thread(() -> {
                say2();
                System.out.println("----------" + Math.random() + "----------");
            }).start();
        }
    }

```



#### 2、实例方法锁

```java
public synchronized void say1() {
        System.out.println("say1");
    }

public static void main(String[] args) {
        for (int i = 0; i < 50; i++) {
            new Thread(()->{
                Test test = new Test();
                /*锁不住，因为实例方法锁的是实例对象，
                每次循环新线程的时候都会new一个新的对象，
                实例对象不同，锁不同，就锁不住*/
                //正确的做法是new一个对象在循环之外，然后在循环中调用方法；还可以将test定义成静态final，然后直接使用
                test.say1();
                System.out.println("----------"+ Math.random() +"----------");
            }).start();
        }
    }

//如果在方法中直接锁
public void say1() {
        synchronized(this){
            ThreadUtils.sleep(100);
            System.out.println("say1");
        }
    }

```



#### 3、代码块锁

```java
public static void main(String[] args) {
        Test test = new Test();
        for (int i = 0; i < 50; i++) {
            new Thread(()->{
                synchronized (Test.class){//不能使用this，因为静态方法中没有this的概念
                    ThreadUtils.sleep(100);
                    System.out.println(2);
                    System.out.println("----------"+ Math.random() +"----------");
                }

            }).start();
        }
    }


//也可以使用监视者更换Test.class，在本类中使用MONITOR，不在的时候使用Test.MONITOR
private static final Object MONITOR = new Object();//监视者

```



### 2、升级的四种锁

> 升级锁的四种锁

> 只有一个卫生间，盘古、盘古+女娲、盘古+女娲+10亿人

- `无锁`没有对象就不需要加锁
- `偏向锁`只有一个线程
- `轻量级锁`少量线程竞争小多次尝试，自旋的方式来获取锁，因为线程挂起唤醒是需要消耗资源的，少量线程就让一直尝试
  - 注：挂起线程和恢复线程的时候都需要转入内核态进行操作，给系统的并发性带来很大的压力。
- `重量级锁`大量线程的时候自旋也是消耗大量资源的方式，只能选择排队挂起线程的方式,使用



![image-20210831172935098](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210831172935098.png)

每个对象都有一个自己的Mark Word，Mark Word记录了实例对象如果作为一把锁的锁标志位，



> JVM一般是这样使用锁和Mark Word的：

1，当没有被当成锁时，这就是一个普通的对象，Mark Word记录对象的HashCode，锁标志位是01，是否偏向锁那一位是0。

2，当对象被当做同步锁并有一个线程A抢到了锁时，锁标志位还是01，但是否偏向锁那一位改成1，前23bit记录抢到锁的线程id，表示进入偏向锁状态。

3，当线程A再次试图来获得锁时，JVM发现同步锁对象的标志位是01，是否偏向锁是1，也就是偏向状态，Mark Word中记录的线程id就是线程A自己的id，表示线程A已经获得了这个偏向锁，可以执行同步锁的代码。

4，当线程B试图获得这个锁时，JVM发现同步锁处于偏向状态，但是Mark Word中的线程id记录的不是B，那么线程B会先用CAS操作试图获得锁。如果抢锁成功，就把Mark Word里的线程id改为线程B的id，代表线程B获得了这个偏向锁，可以执行同步锁代码。如果抢锁失败，则继续执行步骤5。

5，偏向锁状态抢锁失败，代表当前锁有一定的竞争，偏向锁将升级为轻量级锁。JVM会在【当前线程】的线程栈中开辟一块单独的空间，里面保存指向对象锁Mark Word的指针，也叫锁记录（lock record），同时在对象锁Mark Word中保存指向这片空间的指针。上述两个保存操作都是CAS操作，如果保存成功，代表线程抢到了同步锁，就把Mark Word中的锁标志位改成00，可以执行同步锁代码。如果保存失败，表示抢锁失败，竞争太激烈，继续执行步骤6。

6，轻量级锁抢锁失败，JVM会使用自旋锁，自旋锁不是一个锁状态，只是代表不断的重试，尝试抢锁。从JDK1.7开始，自旋锁默认启用，自旋次数由JVM决定。如果抢锁成功则执行同步锁代码，如果失败则继续执行步骤7，自旋默认10次。

7，自旋锁重试之后如果抢锁依然失败，同步锁会升级至重量级锁，锁标志位改为10。在这个状态下，未抢到锁的线程都会被阻塞排队。当后续线程尝试获取锁时，发现被占用的锁是重量级锁，则直接将自己挂起（而不是忙等）进入阻塞状态，等待将来被唤醒。就是所有的控制权都交给了操作系统，由操作系统来负责线程间的调度和线程的状态变更。而这样会出现频繁地对线程运行状态的切换，线程的挂起和唤醒，从而消耗大量的系统资源。



### 3、死锁

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

public class DeadLock {
    public static final Object MONITOR1 = new Object();
    public static final Object MONITOR2 = new Object();

    public static void main(String[] args) {
        new Thread(()->{
            synchronized (MONITOR1){
                System.out.println(Thread.currentThread().getName() + "获取了一号锁");

                ThreadUtils.sleep(100);
                synchronized (MONITOR2){
                    System.out.println(Thread.currentThread().getName() + "获得了二号锁");
                }
            }
        }, "Thread1").start();
        new Thread(()->{
            synchronized (MONITOR2){
                System.out.println(Thread.currentThread().getName() + "获取了二号锁");

                ThreadUtils.sleep(100);
                synchronized (MONITOR1){
                    System.out.println(Thread.currentThread().getName() + "获得了一号锁");
                }
            }
        }, "Thread2").start();
    }
}


```



### 4、线程重入

线程重入的意思就是任意线程在获得锁之后，再次获得该锁不会被该锁阻塞

```java
public class Test {
    private static final Object M1 = new Object();
    private static final Object M2 = new Object();

    public static void main(String[] args) {
        new Thread(() -> {
            synchronized (M1){
                synchronized (M2){
                    synchronized (M1){
                        synchronized (M2){
                            System.out.println("hello lock");
                        }
                    }
                }
            }
        }).start();
    }
}

```



### 5、wait和notify

必须要持有这把锁才可以进行等待和唤醒

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

public class WaitLock {
    public static final Object MONITOR = new Object();

    public static void main(String[] args) {
        new Thread(()->{
            synchronized (MONITOR){
                System.out.println("线程一开始了");
                try {
                    MONITOR.wait();//等待就会释放锁  //()可以有参数，表示等待的时间
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println("线程一结束了");
            }
        }).start();

        new Thread(()->{
            synchronized (MONITOR){
                System.out.println("线程二开始了");
                MONITOR.notify();//随机唤醒一个持有锁的进程，如果是notifyAll就是唤醒所有持有者
                ThreadUtils.sleep(3000);//sleep虽然都不会释放锁，但是会释放cpu的计算资源
                System.out.println("线程二结束了");//唤醒了也需要线程二结束后释放锁线程一才可以使用
            }
        }).start();
    }
}


```

### 6、线程方法

#### Thread方法

(1)sleep

(2)yield(让出上厕所的当前权力，然后和其他线程重新争抢)

```java
package com.ydlclass.lock;

public class YieldTest {
    public static int COUNT1 = 0;
    public static int COUNT2 = 0;

    public static void add1() {
        System.out.println(Thread.currentThread().getName() + ":" + COUNT1++);
    }

    public static void add2() {
        System.out.println(Thread.currentThread().getName() + ":" + COUNT2++);
    }

    public static void main(String[] args) {
        new Thread(() -> {

            for (int i = 0; i < 100; i++) {
                add1();
                Thread.yield();
            }

        }, "t1").start();
        new Thread(() -> {
            for (int i = 0; i < 100; i++) {
                add2();
            }
        }, "t2").start();
    }
}
//输出先是大量的t1，然后是大量的t2穿插少量的t1，之后是剩余的t1

```

#### 线程实例方法

join()：是线程的方法，程序会阻塞在这里等待这个线程执行完毕



#### Object对象锁方法

wait()：释放cpu资源，同时释放锁

notify()：唤醒等待中的程序

notifyAll()：唤醒所有等待中的程序



### 7、退出线程

(1)使用标记位退出线程—常用的是使用标记位优雅的停止线程

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

public class ExitTest {
    private volatile static boolean flag = true;

    public static void main(String[] args) {
        new Thread(()->{
            while(flag){
                System.out.println(111);
            }
        }).start();
        ThreadUtils.sleep(2000);
        flag = false;//使用volatile进行修饰，改变的时候内存中的内容也会被改变
    }
}


```



### 8、LockSupport工具

LockSupport是一个线程工具类，所有的方法都是静态方法，可以阻塞指定线程和唤醒指定线程

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

import java.util.concurrent.locks.LockSupport;

public class LockSupportTest {
    public static void main(String[] args) {
        Thread thread = new Thread(() -> {
            System.out.println(1);
            ThreadUtils.sleep(1000);
            System.out.println(2);
            LockSupport.park("线程停止了");//停止的时候传进一些信息
            System.out.println(3);
        });
        thread.start();

        ThreadUtils.sleep(5000);
        System.out.println("过了5s");
        Object blocker = LockSupport.getBlocker(thread);//得到停止时传入的信息，只要thread实例还在，就能得到传入的信息
        System.out.println(blocker);
        LockSupport.unpark(thread);//唤醒指定的线程  notify唤醒的是持有锁的随机线程
    }
}

```

### 9、Lock(是个接口)锁

重要方法：

```java
// 获取锁  
void lock()   

// 仅在调用时锁为空闲状态才获取该锁，可以响应中断  
boolean tryLock()   

// 如果锁在给定的等待时间内空闲，并且当前线程未被中断，则获取锁  
boolean tryLock(long time, TimeUnit unit)   

// 释放锁  
void unlock()  

```



> 获取锁的方法

```java
Lock lock = ...;
lock.lock();
try{
    //处理任务
}catch(Exception ex){

}finally{
    lock.unlock();   //释放锁  //释放资源是finally最重要的功能之一
}

```

```java
Lock lock = ...;
if(lock.tryLock()) {
     try{
         //处理任务
     }catch(Exception ex){

     }finally{
         lock.unlock();   //释放锁
     } 
}else {
    //如果不能获取锁，则直接做其他事情
}

```

#### (1)ReentrantLock

> Lock的实现类 ReentrantLock

ReentrantLock，可重入锁(线程获取过这把锁之后再获取这把锁就没有障碍了)。ReentrantLock是实现了Lock接口的类，并且ReentrantLock提供了更多的方法实现线程同步。下面通过一些实例学习如何使用 ReentrantLock。

```java
private static final Lock lock = new ReentrantLock();
    public void say1() {
        lock.lock();
        try{
            ThreadUtils.sleep(100);
             System.out.println("say1");
        } finally {
            lock.unlock();
        }
    }

```



#### (2)ReadWriteLock(读写锁)

对于一个应用而言，一般情况读操作是远远要多于写操作的，同时如果仅仅是读操作没有写操作的情况下数据又是线程安全的，读写锁给我们提供了一种锁，读的时候可以很多线程同时读，但是不能有线程写，写的时候是独占的，其他线程既不能写也不能读。在某些场景下能极大的提升效率。

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

import java.util.Random;
import java.util.concurrent.locks.ReentrantReadWriteLock;

public class ReadAndWriteLockTest {
    public static ReentrantReadWriteLock lock = new ReentrantReadWriteLock();
    public static int COUNT = 1;

    public static void main(String[] args) {
        Runnable read = ()->{//
          ReentrantReadWriteLock.ReadLock readLock = lock.readLock();//读的锁
          readLock.lock();
          try {
              ThreadUtils.sleep(2000);
              System.out.println("我在读数据" + COUNT);
          }finally {
              readLock.unlock();
          }
        };
        Runnable write = ()->{//
            ReentrantReadWriteLock.WriteLock writeLock = lock.writeLock();//写的锁
            writeLock.lock();
            try {
                ThreadUtils.sleep(2000);
                System.out.println("我在写数据" + ++COUNT);
            }finally {
                writeLock.unlock();
            }
        };
        for (int i = 0; i < 500; i++) {
            Random random = new Random();
            int flag = random.nextInt(100);
            if (flag > 20){
                new Thread(read, "read").start();
            } else {
                new Thread(write, "write").start();
            }
        }
    }
}

```

### 10、Lock锁的原理—cas和aqs

#### (1)并发编程的三大特性

原子性

- 原子操作定义：原子操作可以是一个步骤，也可以是多个操作步骤，但是其顺序不可以被打乱，也不可以被切割而只执行其中的一部分（不可中断性）。将整个操作视为一个整体是原子性的核心特征。原子性不仅仅是多行代码，也可能是多条指令。
- 存在竞争条件，线程不安全，需要转变原子操作才能安全。方式：上锁、循环CAS；上例只是针对一个变量的原子操作改进，我们也可以实现更大逻辑的原子操作。

可见性

- 不同的线程之间变量的可见性

有序性

- 代码乱序执行
- volatile：可以保证可见性和有序行
- synchronized和Lock：可以保证`原子性、可见性、有序性`
- `public static volatile int COUNT = 0;`
- 静态的可以保证共享变量
- final保证变量不可以被修改
- volatile保证可见性和有序性

#### (2)volatile不能保证原子性的证明

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

public class AtomicTest {
    public static volatile int COUNT = 0;

    public static void main(String[] args) {
        for (int i = 0; i < 50; i++) {
            new Thread(() -> {
                //50个线程同时等待10ms
                ThreadUtils.sleep(30);//如果不等待，因为线程执行的代码很少。就不会产生并行的效果，让一个线程稍微等一下，产生并行效果
                /**
                 * COUNT是静态变量，存放在方法区中，
                 * 每个线程使用的时候会从方法区中拿出来放进为线程分配的私有的栈空间中
                 * ①从方法区取数
                 * ②压进进程的栈
                 * ③弹栈出来进行加
                 * ④结果压栈
                 * ⑤把结果赋值给方法区的COUNT
                 * volatile只能保证这几个步骤不是乱序的——有序性
                 * volatile只能保证取值的时候是在主存中拿的——可见性
                 */
                COUNT++;

            }).start();
        }
        ThreadUtils.sleep(3000);
        System.out.println(COUNT);
    }
}

```

- 如果多线程对数字进行操作可以使用期望值，如果不是期望值就自旋重试

(2)cas

代码模拟cas，多个线程使用一个值会出现问题，但是添加一个静态方法，在每次使用的时候进行比较，将拿到线程栈的值和方法区中的值进行对比，如果一致就进行赋值，不一致就自旋(取值，对比，赋值)

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

public class AtomicTest {
    public static volatile int COUNT = 0;

    //必须要加synchronized
    public static synchronized boolean compareAndSwap(int date, int update) {
        if (date == COUNT) {//如果期望值和COUNT一样就返回正确
            COUNT = update;
            return true;
        } else {
            return false;
        }
    }

    public static void main(String[] args) {
        for (int i = 0; i < 50; i++) {
            new Thread(() -> {
                //50个线程同时等待10ms
                ThreadUtils.sleep(30);//如果不等待，因为线程执行的代码很少。就不会产生并行的效果，让一个线程稍微等一下，产生并行效果
                //模拟自旋
                boolean flag = false;
                while (!flag) {
                    flag = compareAndSwap(COUNT, COUNT + 1);
                }

            }).start();
        }
        ThreadUtils.sleep(3000);
        System.out.println(COUNT);
    }
}


```

#### (3)CAS(比较并交换compareAndSet)

对变量修改的原子性操作问题

cas就是比较并交换，上面的代码中可能值不是想要的值，可以多加一步先把拿到的值和想要修改之前的值(期望值)进行比较，如果不是就进行自旋，不用挂起线程，然后再改成upDate，是通过cpu实现的。

CAS，compare and swap的缩写，中文翻译成比较并交换，我发现jdk11以后改成了compare and set。

它的思路其实很简单，就是给一个元素赋值的时候，先看看内存里的那个值到底变没变，如果没变我就修改，变了我就不改了，其实这是一种无锁操作，不需要挂起线程，无锁的思路就是先尝试，如果失败了，进行补偿，也就是你可以继续尝试。这样在少量竞争的情况下能很大程度提升性能。

![image-20210902213010773](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210902213010773.png)

Java中的CAS是通过sun.misc.Unsafe类提供的。Unsafe中的CAS

```java
/**
*Object var1      你要修改哪个对象的成员变量
*long offset      这个值在这个对象中的偏移量
*Object expected  期望值
*Object x         实际值
*/
public final native boolean compareAndSwapObject(Object var1, long var2, Object var4, Object var5);
public final native boolean compareAndSwapInt(Object var1, long var2, int var4, int var5);
public final native boolean compareAndSwapLong(Object var1, long var2, long var4, long var6);

```



但是CAS还是有几个缺点：

1. ABA问题。当第一个线程执行CAS操作，尚未修改为新值之前，内存中的值已经被其他线程连续修改了两次，使得变量值经历 A -> B -> A的过程。绝大部分场景我们对ABA不敏感。解决方案：添加版本号作为标识，每次修改变量值时，对应增加版本号； 做CAS操作前需要校验版本号。JDK1.5之后，新增AtomicStampedReference类来处理这种情况。
2. 循环时间长开销大。如果有很多个线程并发，CAS自旋可能会长时间不成功，会增大CPU的执行开销。
3. 只能对一个变量进行原子操作。JDK1.5之后，新增AtomicReference类来处理这种情况，可以将多个变量放到一个对象中。

**volatile和cas进行配合实现了线程安全**

竞争不激烈的时候使用，如果竞争激烈就会产生大量的自旋



#### (4)aqs(抽象队列同步器)—aqs知识铺垫(源码讲解)

抽象类中维护了个队列，队列是用来实现同步器的

同步就是为了让多个线程争抢锁的时候一个一个的来

![image-20210903114020851](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210903114020851.png)



![image-20210902222055510](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210902222055510.png)



- aqs是一个双向链表
- 很完美的解决了线程排队的问题

## 四、jue并发编程包

### 一、原子类

#### 1、认识 Atomic 原子类

​		Atomic 翻译成中文是原子的意思。在化学中，原子是构成一般物质的最小单位，是不可分割的。而在这里，Atomic 表示当前操作是不可中断的，即使是在多线程环境下执行，Atomic 类，是具有原子操作特征的类。

​		Java 的原子类都存放在并发包 `java.util.concurrent.atomic` 下。

#### 2、 JUC 包中的原子类

> 基本类型

使用原子的方式更新基本类型

- AtomicInteger：整形原子类
- AtomicLong：长整型原子类
- AtomicBoolean：布尔型原子类

> 数组类型

使用原子的方式更新数组里的某个元素

- AtomicIntegerArray：整形数组原子类
- AtomicLongArray：长整形数组原子类
- AtomicReferenceArray：引用类型数组原子类

> 引用类型

- AtomicReference：引用类型原子类
- AtomicStampedReference：原子更新引用类型里的字段原子类
- AtomicMarkableReference ：原子更新带有标记位的引用类型

> 对象的属性修改类型**

- AtomicIntegerFieldUpdater：原子更新整形字段的更新器
- AtomicLongFieldUpdater：原子更新长整形字段的更新器
- AtomicStampedReference：原子更新带有版本号的引用类型。该类将整数值与引用关联起来，可用于解决原子的更新数据和数据的版本号，以及解决使用 CAS 进行原子更新时可能出现的 ABA 问题

#### 3、AtomicInteger的使用

AtomicInteger为什么能保证线程的安全性

- value使用volatile进行修饰，保证了内存可见性和静止指令重排
- 修改value的方法都使用了cas，保证了原子性
- 所以说Atomic是线程安全的类

```java
package com.ydlclass.lock;

import com.ydlclass.ThreadUtils;

import java.util.concurrent.atomic.AtomicInteger;

public class AtomicIntegerTest {
    private static AtomicInteger atomicInteger = new AtomicInteger(0);

    public static void main(String[] args) {
        for (int i = 0; i < 50; i++) {
            new Thread(()->{
                ThreadUtils.sleep(20);
                atomicInteger.addAndGet(1);
            }).start();
        }
        ThreadUtils.sleep(1000);
        System.out.println(atomicInteger.get());
    }
}

```

## 五、线程池

我们开辟线程、关闭线程、挂起线程都是要消耗资源的，在运行系统的时候就给一些线程，就放在线程池中。

就是安排线程干活的，线程的数量也是有限的，如果线程不够了，需要让程序等一等，等有空闲的线程了再进行线程安排。

很多了逻辑来源于我们的现实，想象成一个公司，线程池中的线程就好像是一个个的员工。

### 一、jdk自带的四种线程池

`ExecutorService executorService = Executors.newCachedThreadPool();//外包线程池`

Java通过Executors提供四种线程池，分别为：

1. `newCachedThreadPool`**(空壳公司)**创建一个可缓存线程池，如果线程池长度超过处理需要，可灵活回收空闲线程，若无可回收，则新建线程。—优先使用回收回来的线程
2. `newFixedThreadPool`  **(线程池的长度确定)**创建一个定长线程池，可控制线程最大并发数，超出的线程会在队列中等待。
3. `newScheduledThreadPool` 创建一个定长线程池，支持定时及周期性任务执行。
4. `newSingleThreadExecutor` 创建一个单线程化的线程池，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序执行。

#### 1、七个参数【重要】

|                 |                                                              |
| --------------- | ------------------------------------------------------------ |
| corePoolSize    | 指定了线程池里的线程数量，核心线程池大小—创建下就有多少线程  |
| maximumPoolSize | 指定了线程池里的最大线程数量                                 |
| keepAliveTime   | 当线程池线程数量大于corePoolSize时候，多出来的空闲线程，多长时间会被销毁 |
| unit            | 时间单位，TimeUnit                                           |
| workQueue       | 任务队列，用于存放提交但是尚未被执行的任务—下面的Array、Linked |
| threadFactory   | 线程工厂，用于创建线程，线程工厂就是给我们new线程的          |
| handler         | 所谓拒绝策略，是指将任务添加到线程池中时，线程池拒绝该任务所采取的相应策略 |

> 常见的工作队列我们有如下选择，这些都是阻塞队列，阻塞队列的意思是，当队列中没有值的时候，取值操作会阻塞，一直等队列中产生值。

- ArrayBlockingQueue：基于数组结构的有界阻塞队列(任务队列，可以放任务、Object、什么都可以)，FIFO。
- LinkedBlockingQueue：基于链表结构的有界阻塞队列，FIFO。—一直使用直到OOM(内存爆了)

> 线程池提供了四种拒绝策略：

- AbortPolicy：直接抛出异常，默认策略；—**常用**
- CallerRunsPolicy：用调用者所在的线程来执行任务；
- DiscardOldestPolicy：丢弃阻塞队列中最靠前的任务，并执行当前任务；
- DiscardPolicy：直接丢弃任务；

> 线程池按以下行为执行任务

![image-20210902224805090](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/java%E9%AB%98%E5%B9%B6%E5%8F%91.assets/image-20210902224805090.png)

我们来看一下这四种线程池都是使用`ThreadPoolExecutor`进行构造的:

> newCachedThreadPool

```javascript
public static ExecutorService newCachedThreadPool() {
    return new ThreadPoolExecutor(0, Integer.MAX_VALUE,
                                  60L, TimeUnit.SECONDS,
                                  new SynchronousQueue<Runnable>());
}

```

通过指定参数,返回ThreadPoolExecutor来实现.  参数为:

```javascript
 核心线程池大小=0
 最大线程池大小为Integer.MAX_VALUE
 线程过期时间为60s
 使用SynchronousQueue作为工作队列.

```

所以线程池为0-max个线程,并且会60s过期,实现了可以缓存的线程池。

#### 2、自定义线程池—多看，看思路





#### 3、线程同步

CountDownLatch(倒计时器)和CyclicBarrier(循环栅栏)

CountDownLatch实现线程同步

- countDown自减1
- await等待减到0



### 二、单例(双重检查锁)

懒汉式实现单例线程不安全的原因：方法是放进方法区中的，所以可能会被多个线程进行调用，会出现问题

不严谨的就是可能会出现对象半实例化

- 引用指向空间的指令放进init指令之前，会产生空

```java
package com.ydlclass.pool;

public class Singleton {
    private static volatile Singleton instance;//添加volatile，进制指令重排，使用双重锁，形成完美的单例

    private Singleton() {

    }

    public static Singleton getInstance() {
        //检查instance是否被构建
        if (instance == null) {//不加的时候会造成资源消耗
            synchronized (Singleton.class) {//第一次初始化instance的时候需要排队，但是没有外面的if就是所有的线程都在这里排队了,只有instance是空的时候才需要排队
                //如果没有这个会产生多个instance
                if (instance == null) {
                    instance = new Singleton();


                }
            }
        }
        return instance;

    }
}

```



# 第十二章 树

## 一、基本概念

二叉树：每个节点最多有两个子节点

度：拥有孩子节点的个数

层：最上面是第一层，往下累加

深度：最大层数

满二叉树：所有的非叶子节点都有左右孩子，所有的叶子节点都在同一层

完全二叉树：高级二叉树，只能丢失右边的叶子节点

斜树也是二叉树

二叉树的性质



## 二、二叉树的存储方式

满二叉树可以根据编号放进数组，普通二叉树可以在非满二叉树位置存入null，

### 1、二叉树的【递归】遍历

- 前序遍历
- 中序遍历
- 后序遍历
- 层次遍历

使用递归进行二叉树的遍历会在每次调用方法的时候在栈帧创建一个空间，会造成资源浪费，如果能力可以，可以使用堆栈的方法进行遍历

```java
package com.ydlclass;

//           递归      二叉树
public class RecursiveBinaryTree {

    private static class Node {
        Integer date;
        Node LeftNode;
        Node RightNode;

        public Node() {
        }

        public Node(Integer date) {
            this.date = date;
        }

        /**
         * 传入根节点
         * 开始遍历这个树
         * 判断是不是叶子节点，不是的话就遍历他的左子树，使用相同的方式
         *
         * @param node
         */
        private void recursive(Node node) {
            if (node == null) {
                return;
            }
            recursive(node.LeftNode);
            recursive(node.RightNode);
        }

        //先序遍历
        private static void preOrder(Node node) {
            if (node == null) {
                return;
            }
            System.out.println(node.date);
            preOrder(node.LeftNode);
            preOrder(node.RightNode);
        }

        //中序遍历
        private static void inOrder(Node node) {
            if (node == null) {
                return;
            }
            inOrder(node.LeftNode);
            System.out.println(node.date);
            inOrder(node.RightNode);
        }

        //后序遍历
        private static void postOrder(Node node) {
            if (node == null) {
                return;
            }
            postOrder(node.LeftNode);
            postOrder(node.RightNode);
            System.out.println(node.date);

        }


        public static void main(String[] args) {
            Node root = new Node(1);
            root.LeftNode = new Node(2);
            root.RightNode = new Node(3);
            root.LeftNode.LeftNode = new Node(4);
            root.LeftNode.RightNode = new Node(5);
            root.RightNode.LeftNode = new Node(6);
            root.RightNode.RightNode = new Node(7);
            inOrder(root);
        }

    }
}


```

### 2、使用栈实现二叉树的遍历

- 压栈、弹栈的过程就是把这个树变成一个线性表
- 按照一定的规律顺序进行压栈弹栈就会实现
- 先序遍历就是先遍历根节点，先把根节点压入栈，然后弹出来，再压入左子树的根节点，弹出，但是防止右子树丢失，在压入左子树之前应该把右子树先压入栈中，再压入左节点，再弹出左节点，防止数据丢失
- 防止找不到数，需要一个Node指向当前弹出的节点

```java
//用栈实现二叉树的先序遍历
        //先序遍历是先遍历根节点，然后是左子树，最后是右子树
        //先压入根节点，然后弹出，压入右子树，压入左子树，弹出左子树
        private static void pre(Node node) {
            Stack<Node> stack = new Stack<>();
            stack.push(node);//根节点压入栈中

            //栈不为空就一直运行
            while (!stack.isEmpty()) {
                //弹出当前树的根节点
                //保存弹出的节点，为了保存数据
                //弹出的实际是一个根节点—弹出去之后处理他的子树
                node = stack.pop();
                System.out.println(node.date);
                //先把右边保存进栈
                if (node.RightNode != null) {
                    stack.push(node.RightNode);
                }
                //保存左子树
                if (node.LeftNode != null) {
                    stack.push(node.LeftNode);
                }
            }

        }

```

### 3、使用队列实现二叉树的遍历



## 三、其他树的分类

### 1、二叉查找树【重点】

特征：

1. 若左子树不为空，那么左子树所有节点的值小于均小于他的根节点的值。
2. 若右子树不为空，那么右子树的所有节点的值大于根节点的值。
3. 左右子树也分别为二叉排序树。
4. 没有键值相等的节点。
5. 整体是一个查找二叉树，子树也是查找二叉树。

```java

```

### 2、平衡二叉树

特征：

1. 满足查找二叉树的条件；
2. 要么是个空树，要么其根节点的左右子树的深度差不超过1；
3. 其左右子树都是平衡二叉树；
4. 平衡二叉树的查找效率极高
5. 需要考虑维护这棵树的成本(树的旋转)和检索这棵树的成本的选择

### 3、红黑树

在平衡二叉树的基础上每个节点又增加了一个颜色属性(使用flag标记位)

特征：

1. 根节点只能是黑色的
2. 红黑树的所有的叶子节点都要添加两个空的左右子节点，所有的空节点都是黑色的
3. 其他节点要么是红色的，要么是黑色的，红色节点的父节点和子节点都是黑色的，即黑红相间
4. 任意一棵子树中，从根节点从下走，走到空节点的路径上所经过的黑节点的数目相同，从而保证了是一颗平衡二叉树
5. 左子树和右子树的层高差距不能超过一半

![20190701211820780](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/javase%E5%AD%A6%E4%B9%A0%E5%85%A8%E8%B5%84%E6%96%99.assets/20190701211820780.png)

### 4、B-树也叫B树(多叉树)

B-树是一种平衡多路查找树，它在文件系统中很有用。一棵m阶B-树（图d为4阶B-树），具有下列性质：

（1）树中每个节点至多有m棵子树；
（2）若根节点不是叶子节点，则至少有2棵子树；
（3）除根节点之外的所有非终端节点至少有![img](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/javase%E5%AD%A6%E4%B9%A0%E5%85%A8%E8%B5%84%E6%96%99.assets/2011112215223323.jpg)棵子树；
（4）每个节点中的信息结构为（A0,K1,A1,K2......Kn,An），其中n表示关键字个数，Ki为关键字，Ai为指针；
（5）所有的**叶子节点都出现在同一层次上**，且不带任何信息，也是为了保持算法的一致性。

![20190701211851956](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/javase%E5%AD%A6%E4%B9%A0%E5%85%A8%E8%B5%84%E6%96%99.assets/20190701211851956.png)

### **5.B+树**

B+数是B-树的一种变形，它与B-树的差别在于（图e为3阶B+树）：
（1）有n棵子树的节点含有n个关键字；
（2）所有的叶子节点包含了全部关键字的信息，及指向这些关键字记录的指针，**且叶子节点本身按关键字大小自小到大顺序链接**；
（3）所有非终端节点可以看成是索引部分，节点中仅含有其子树（根节点）中最大（或最小）关键字，所有B+树更像一个索引顺序表；
（4）对B+树进行查找运算，一是从最小关键字起进行顺序查找，二是从根节点开始，进行随机查找。

![20190701211919875](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/javase%E5%AD%A6%E4%B9%A0%E5%85%A8%E8%B5%84%E6%96%99.assets/20190701211919875.png)





# 第十四章 集合框架

## 一、集合的继承结构

分成两个部分，一边是线性表，一边是映射(Map)(连线题、索引目录)

![image-20210717194609366](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9B%86%E5%90%88.assets/image-20210717194609366.png)

哈希：无序

- ArrayList基于数组实现的线性表
- LinkList基于链表的
- sout自动调用toString

### 1、List

```java
ArrayList<String> arrayList = new ArrayList<>();

```

```java
LinkList<String>  linkList = new LinkList<>();

```

```java
List<String> list = new ArrayList<>();//父类引用指向子类对象
静态分派和动态分派的过程

```

```java
package com.ydlclass;

import java.util.ArrayList;

public class Test {
    public static void add() {
        ArrayList<String> arrayList = new ArrayList<>();
        arrayList.add("a");
        arrayList.add("b");

        ArrayList<String> arrayList1 = new ArrayList<>();
        arrayList1.add("c");
        arrayList1.add("d");
        arrayList.addAll(1, arrayList1);

        System.out.println(arrayList);
    }

    public static void del() {
        ArrayList<String> arrayList = new ArrayList<>();
        arrayList.add("a");
        arrayList.add("b");
        arrayList.remove("b");//删除指定的元素

        System.out.println(arrayList);

    }

    public static void main(String[] args) {
        add();
        System.out.println("--------------");
        /**
         * 删除指定元素、指定下标、所有
         */
        del();
    }
}


```

### 2、HashSet

- 会自动删除重复的
- 乱序的

```java
package com.ydlclass;

import java.util.HashSet;

public class SetTest {
    public static void main(String[] args) {
        HashSet<String> hashSet = new HashSet<>();
        hashSet.add("a");
        hashSet.add("b");
        hashSet.add("c");
        hashSet.add("e");
        hashSet.add("e");
        hashSet.add("f");
        hashSet.add("h");
        hashSet.add("i");
        hashSet.add("j");
        hashSet.add("r");
        System.out.println(hashSet);
    }
}

```

- 如果需要删除List的相同的元素，对数据的顺序没有要求，先创建一个Set，将List通过addAll添加进Set，再用addAll添加进List

```java
package com.ydlclass;

import java.util.HashSet;
import java.util.LinkedList;
import java.util.Set;

public class SetTest {
    public static void main(String[] args) {
        LinkedList<String> linkedList = new LinkedList<>();
        linkedList.add("a");
        linkedList.add("b");
        linkedList.add("c");
        linkedList.add("e");
        linkedList.add("e");
        linkedList.add("f");
        linkedList.add("h");
        linkedList.add("i");
        linkedList.add("j");
        linkedList.add("r");
        System.out.println(linkedList);
        //左手倒右手
        Set<String> strings = new HashSet<>();
        strings.addAll(linkedList);
        linkedList.clear();//先清空
        linkedList.addAll(strings);

        System.out.println(strings);

    }
}


```

### 3、Map(映射)

- 有两个值key和value
- 使用Map的时候key不能重复

```java
Map<String, User> map = new HashMap<>();

```

- 可以通过key找到value，但是不能通过value找到key

```java
package com.ydlclass;

import java.util.HashMap;
import java.util.Map;

public class MapTest {
    public static void main(String[] args) {
        Map<String, User> map = new HashMap<>();
        map.put("2021zxx0501", new User("zhangsan1", 12));//put是赋值
        map.put("2021zxx0502", new User("zhangsan2", 12));
        map.put("2021zxx0503", new User("zhangsan3", 12));
        //如果key一样，value会覆盖之前的值
        map.put("2021zxx0501", new User("zhangsan4", 12));
        System.out.println(map);//get是取值
    }
}


```

## 二、源码分析

### 1、查看List的grow()方法

- 按照1.5倍扩容的
- 新的容量小于最小容量要求的时候，直接让新的容量等于最小容量
- 第二个判断是判断容量是不是特别大，是否会出现越界和已经越界
- 最后是创建一个长度为newCapacity长度的数组，把旧数组的元素放进新数组，改变引用

### 2、查看LinkedList的源码

- 添加的源码
- 删除的源码

### 3、查看Hashmap的源码

#### (1)基本了解(灯笼)

![image-20210719104716936](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9B%86%E5%90%88.assets/image-20210719104716936.png)

- 了解存储的结构—hashmap构造的时候会创建长度为16的数组 ，根据hash返回的int选择保存的位置，如果有重复的，发生hash碰撞，就变成链表，接在next之后，如果超过8个，自动变成一个红黑树，变成红黑树之后，节点膨胀，一个节点表示的东西变多

> 简而言之是这样的（不太对，但是有个大概的了解）：

第一步：hashmap构造时（其实不是构造的时候）会创建一个长度为16数组，名字叫table，也叫hash表;

第二步：hashmap在插入数据的时候，首先根据key计算hashcode，然后根据hashcode选择一个槽位。

​		假设hashmap使用取余的方式计算。（事实上，hashmap不是）

​		我们都知道hashcode会返回一个int值，使用int值除以16取余就能得到一个0~15的数字，就能去定一个具体的槽位。

第三步：确定了具体的槽位之后，我们就会封装一个node（节点），里边保存了hash，key，value等数据存入这个槽中。

第四步：当存入新的数据的时候，使用新的hash计算的槽位发现已经有了数据，这个现象叫做hash碰撞，会以链表的形式存储。

第五步：当链表的个数到达了8个，链表开始树化，变成一个红黑树。

通过这五个步骤，大家先有一个基本的了解，更多的细节我们下来看源码。

#### (2)成员变量

```java
// 默认容量
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16

// 最大容量
static final int MAXIMUM_CAPACITY = 1 << 30;

// 默认的加载因子
static final float DEFAULT_LOAD_FACTOR = 0.75f;

// 默认的一个树化的一个阈值 （THRESHOLD 阈值）
static final int TREEIFY_THRESHOLD = 8;

// 非树化的一个阈值
static final int UNTREEIFY_THRESHOLD = 6;

// 树化的最小容量，能看到一些信息，树化除了链表长度，对容量也有要求
static final int MIN_TREEIFY_CAPACITY = 64;

// 存储数据的hash表，就是一个数组
transient Node<K,V>[] table;

// 真实的负载因子
final float loadFactor;

```

#### (3)构造器

```java
// 只是将默认的负载因子传递给了loadFactor
public HashMap() {
    this.loadFactor = DEFAULT_LOAD_FACTOR; // all other fields defaulted
}

// 有传入的初始化容量
public HashMap(int initialCapacity) {
    this(initialCapacity, DEFAULT_LOAD_FACTOR);
}

// 有传入的初始化容量和负载因子
public HashMap(int initialCapacity, float loadFactor) {
    if (initialCapacity < 0)
        throw new IllegalArgumentException("Illegal initial capacity: " +
                                           initialCapacity);
    if (initialCapacity > MAXIMUM_CAPACITY)
        initialCapacity = MAXIMUM_CAPACITY;
    if (loadFactor <= 0 || Float.isNaN(loadFactor))
        throw new IllegalArgumentException("Illegal load factor: " +
                                           loadFactor);
    // 计算新的负载因子和容量
    this.loadFactor = loadFactor;
    this.threshold = tableSizeFor(initialCapacity);
}  



/**
  * 返回一个值，大于等于传入的数字的一个2的次幂的数字，你传入15返回16，传入7返回8、
  * 保证了容量是2的次幂。为了后来计算hash槽做准备
  */
static final int tableSizeFor(int cap) {
    int n = cap - 1;
    n |= n >>> 1;
    n |= n >>> 2;
    n |= n >>> 4;
    n |= n >>> 8;
    n |= n >>> 16;
    return (n < 0) ? 1 : (n >= MAXIMUM_CAPACITY) ? MAXIMUM_CAPACITY : n + 1;
}


static final int tableSizeFor(int cap) {
    // 00010000 11101001 10001001 10000101  -- > 00010000 11101001 10001001 10000100  283,740,549
    // 看完了
    int n = cap - 1;
    // 00010000 11101001 10001001 10000101     n
    // 00001000 01110100 11000100 11000010     右移1位，保障2位是1
    // 00011000 11101101 11001101 11000111     n
    n |= n >>> 1;
    // 00011000 11101101 11001101 11000111     n
    // 00000110 00111011 01110011 01110001     右移2位，保障4位是1
    // 00011110 11111111 11111111 11110111     n
    n |= n >>> 2;
    // 00011110 11111111 11111111 11110111     n
    // 00000001 11101111 11111111 11111111     右移4位，保障8位是1
    // 00011111 11111111 11111111 11111111     n
    n |= n >>> 4;
    // 00011111 11111111 11111111 11111111     n
    // 00000000 00011111 11111111 11111111     右移8位，保障16位是1
    // 00011111 11111111 11111111 11111111     n
    n |= n >>> 8;
    // 00011111 11111111 11111111 11111111     n
    // 00000000 00000000 00011111 11111111     右移8位，保障32位是1
    // 00011111 11111111 11111111 11111111     n
    n |= n >>> 16;
    return  n + 1;
}

```



#### (4)put

- hash算法为什么使用高16位和低16位进行运算，是为了让结果分布更均匀
- 为什么数组长度是2^，只有这种数字-1之后是0后面全是1，然后跟任意数字进行异或运算，得到的数字就会小于要求的长度，就可以用得到下标

```java
public V put(K key, V value) {
    return putVal(hash(key), key, value, false, true);
}

// 第一个关键点：key == null，说明我们的hashmap支持key为null
// 第二个关键点： (h = key.hashCode()) ^ (h >>> 16) ,这一点学完，学完putVal方法再看
// h          1010 0010 0001 1001 0010 1100 1010 1001
// h >>> 16   0000 0000 0000 0000 1010 0010 0001 1001 ( 0010 1100 1010 1001)
// 异或运算     1010 0010 0001 1001 1000 1110 1011 0000 
// 目的： 让高16位和低16位同时参与计算，将来计算hash槽时更加均匀
static final int hash(Object key) {
    int h;
    //会传入具体的Object类型的实参，如果实参重写了hashCode(),就会调用实参的hashCode(),如果没有就调用Object的hashCode()
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}

```

```java
 final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
     // tab很明显就是hash表
     Node<K,V>[] tab; 
     // 就是个引用（指针），
     Node<K,V> p; 
     // 先不要管,n代表hash表的长度（tab）
     int n, i;
     // (tab = table) == null 将hash表赋值给tab，并且判断是不是null
     // 或者长度等于0，我就要扩容，构造没有初始化
     if ((tab = table) == null || (n = tab.length) == 0){
         // 那就扩容，还兼任初始化的责任（16）
         n = (tab = resize()).length;
     }
     // p == null,只不过有个给p赋值的过程
     // p = tab[i = (n - 1) & hash]
     // 其实 i是计算的槽位，你的数据往哪个格子里放
     // (n - 1) & hash 这是真实的计算过程，n确定是一个2的n次幂(100..)，hash是一个int值
     // (n-1)      0000 0000 0000 0000 0000 0000 0000 1111
     // (hash)     0010 0010 0010 0010 0000 0110 0000 1011
     // (result)   0000 0000 0000 0000 0000 0000 0000 1011       
     // 与运算之后的结果就是0~15，正好计算了一个槽位
     // 第一个思考的问题：为什么容量必须是2的次幂？ 0...01...1
     // 第二个思考的问题：为什么使用位移运算而不适用余运算？效率
     // 找到槽位，并且槽位没有数据，就直接newnode放进去
     if ((p = tab[i = (n - 1) & hash]) == null){
         // 创建了一个node
         tab[i] = newNode(hash, key, value, null);
     } else {
         // 只要进入else，说明这个槽位有数据了，就要搞链表了
         // 
         Node<K,V> e;
         // 键，泛型，当前插入数据的键
         K k;
         // 根据p = tab[i = (n - 1) & hash]，知道p是放在槽位上的node
         // p.hash == hash 说明发生了hash碰撞
         // (k = p.key) == key || (key != null && key.equals(k)) 判断的是key重复了
         if (p.hash == hash &&
             ((k = p.key) == key || (key != null && key.equals(k)))){
             // 覆盖
             e = p;
             
         // 判断是不是树形节点
         } else if (p instanceof TreeNode){
             e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
             
         // 否则就是链表的方式
         } else {
             for (int binCount = 0; ; ++binCount) {
                 if ((e = p.next) == null) {
                     // 这不就是链表吗？很明显这是尾插
                     p.next = newNode(hash, key, value, null);
                     if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                         // 树化
                         treeifyBin(tab, hash);
                     break;
                 }
                 // 判断链表中有没有key一样的，覆盖
                 if (e.hash == hash &&
                     ((k = e.key) == key || (key != null && key.equals(k))))
                     break;
                 p = e;
             }
         }
         if (e != null) { // existing mapping for key
             V oldValue = e.value;
             if (!onlyIfAbsent || oldValue == null)
                 e.value = value;
             afterNodeAccess(e);
             return oldValue;
         }
     }
     ++modCount;
     if (++size > threshold)
         resize();
     afterNodeInsertion(evict);
     return null;
 }

```

#### (5)扩容

```java
final Node<K,V>[] resize() {
    Node<K,V>[] oldTab = table;
    // 旧的容量
    int oldCap = (oldTab == null) ? 0 : oldTab.length;
    // 旧的阈值
    int oldThr = threshold;
    int newCap, newThr = 0;
    if (oldCap > 0) {
        // 容量大于最大值就取最大值
        if (oldCap >= MAXIMUM_CAPACITY) {
            threshold = Integer.MAX_VALUE;
            return oldTab;
        
        // 这里体现了扩容的大小
        // newCap = oldCap << 1 相当于2倍
        } else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&
                 oldCap >= DEFAULT_INITIAL_CAPACITY)
            // 阈值月扩容二倍
            newThr = oldThr << 1; // double threshold
    // 旧的阈值大于零
    } else if (oldThr > 0){ // initial capacity was placed in threshold
        // 旧的阈值 = 新的容量
        newCap = oldThr;
       
    // 否则就是初始化，因为 == 0
    } else {               // zero initial threshold signifies using defaults
        // 否则新的容量就是默认的容量
        newCap = DEFAULT_INITIAL_CAPACITY;
        // 新的阈值就是 容量*负载因子
        newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);
    }
    
    // 计算新的阈值，要么是相乘，要么Integer最大值
    if (newThr == 0) {
        float ft = (float)newCap * loadFactor;
        newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?
                  (int)ft : Integer.MAX_VALUE);
    }
    
    // 将计算好的阈值赋值给 threshold
    threshold = newThr;
    @SuppressWarnings({"rawtypes","unchecked"})
    
    // 根据新的容量创建了新的hash表
    Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];
    table = newTab;
    // 以下是重新拷贝的过程
    if (oldTab != null) {
        for (int j = 0; j < oldCap; ++j) {
            Node<K,V> e;
            if ((e = oldTab[j]) != null) {
                oldTab[j] = null;
                if (e.next == null)
                    newTab[e.hash & (newCap - 1)] = e;
                else if (e instanceof TreeNode)
                    ((TreeNode<K,V>)e).split(this, newTab, j, oldCap);
                else { // preserve order
                    Node<K,V> loHead = null, loTail = null;
                    Node<K,V> hiHead = null, hiTail = null;
                    Node<K,V> next;
                    do {
                        next = e.next;
                        if ((e.hash & oldCap) == 0) {
                            if (loTail == null)
                                loHead = e;
                            else
                                loTail.next = e;
                            loTail = e;
                        }
                        else {
                            if (hiTail == null)
                                hiHead = e;
                            else
                                hiTail.next = e;
                            hiTail = e;
                        }
                    } while ((e = next) != null);
                    if (loTail != null) {
                        loTail.next = null;
                        newTab[j] = loHead;
                    }
                    if (hiTail != null) {
                        hiTail.next = null;
                        newTab[j + oldCap] = hiHead;
                    }
                }
            }
        }
    }
    return newTab;
}

```

### 4、HashSet源码

只要理解了hashmap，hashset不攻自破。

（1）首先我们看到hashset内部维护了一个hashmap，其实说明了hashset的实现是基于hashmap的。

```java
private transient HashMap<E,Object> map;

```

（2）我们看到hashset的构造器其实只是new了一个hashmap();

```java
public HashSet() {
    map = new HashMap<>();
}

```

（3）我们以添加为例

```java
private static final Object PRESENT = new Object();
public boolean add(E e) {
    return map.put(e, PRESENT)==null;
}

```

## 三、集合的遍历

### 1、普通for循环

```java
for(int i = 0; i < list.size(); i++){
    System.out.println(list.get(i));
}

```

### 2、迭代器

- 迭代器是一种思想
- iterator
  - hasnext()—是不是有下一个节点
  - next()—得到节点

#### (1)List的遍历

```java
Iterator<String> iterator = linkedList.iterator();
while (iterator.hasNext()){
    String next = iterator.next();
    System.out.println(next);
}

```

```java
Iterator<String> iterator = arrayList.iterator();
while(iterator.hasNext()){
    String next = iterator.next();
    System.out.println(next);
}

```

#### (2)Map的遍历

> 方法一：先把key整理成一个新的集合，然后使用key进行遍历

```java
//第一种方法：把key转成一个集合，再拿到key的迭代器
Set<String> strings = map.keySet();
Iterator<String> iterator = strings.iterator();
while (iterator.hasNext()){
    String next = iterator.next();
    System.out.println("key = " + next);
    System.out.println("value = " + map.get(next));

}

```

> 方法二：使用Entry()方法，得到一个键值对的集合，使用键值对的集合进行遍历

```java
 //第二种方法—调用方法得到键值对
//新的集合，其中放的Entry类型的数据，Entry放的是key和value打包起来的数据
Set<Map.Entry<String, User>> entries = map.entrySet();
Iterator<Map.Entry<String, User>> iterator1 = entries.iterator();
while(iterator1.hasNext()){
    Map.Entry<String, User> next = iterator1.next();
    System.out.println(next);
}

```

### 3、迭代器的原理

- 迭代器就是有以一个游标，刚开始指向头部，然后向后，跟arraylist的size进行对比，如果一样，就代表没有下一个了，linklist的时候，游标的nextNode如果是null，就代表是空，就没有下一个了
- next()—原来游标就是一个下标，有了下标就可以得到数组的值了
- hashSet的本质就是一个hashMap(挂灯笼)
  - 遍历的时候是先进入数组，然后进行链表的遍历—双重for循环
- 查看Iterator<E>的子类ArrayList、LinkedBlocking



### 4、增强for循环——集合的遍历

集合中的增强for循环本质上还是调用的迭代器

`甜甜的语法糖`

在ArrayList的Next方法打断点

```java
/**
 * 因为Map没有迭代器，使用的是Entry的迭代器
* 前面就要拿到每一个Entry，Entry是Map的内部类
*/
for ( Map.Entry<String, User> entry :  map.entrySet()) {
    System.out.println(entry.getKey());
    System.out.println(entry.getValue());
}

```

```java
int[] nums = {1, 2, 3};
for (int num : nums) {
    System.out.println(num);
}

```

### 5、删除集合中的元素

#### (1)使用remove删除指定的元素

```java
arrayList.remove("lucy");

```

#### (2)在for循环时使用remove()

最后输出的时错误的，因为List删除之后后面的元素会自动挪位，挪到前面来

```java
for (int i = 0; i < arrayList.size(); i++) {
    if ("lucy".equals(arrayList.get(i)))
        arrayList.remove(i);
}

```

解决方法一：`指针回调`

```java
for (int i = 0; i < arrayList.size(); i++) {
    if ("lucy".equals(arrayList.get(i))) {
        arrayList.remove(i);
        i--;
    }
}

```

解决方法二：`逆序遍历`

```java
for (int i = arrayList.size()-1; i >= 0; i--) {
    if("lucy".equals(arrayList.get(i)))
        arrayList.remove(i);
}

```

#### (3)使用迭代器进行删除

```java
Iterator<String> iterator = arrayList.iterator();
while(iterator.hasNext()){
    if("lucy".equals(iterator.next()))
        //迭代器中必须使用迭代器的方法进行删除
        iterator.remove();
}

```

```java
Set<Integer> nums = new HashSet<>();
nums.add(1);
nums.add(2);
nums.add(3);
nums.add(4);
nums.add(5);
Iterator<Integer> iterator = nums.iterator();
while (iterator.hasNext()){
    if (iterator.next() > 3)
        iterator.remove();
}
System.out.println(nums);

```

> 删除元素的时候只能使用循环或者迭代器，迭代器中不能使用普通的remove()方法，只能使用迭代器的remove()方法;同样的，循环中只能使用普通的remove()方法，不能使用迭代器的remove()方法；普通循环的删除还有可能出错，所以使用迭代器是一种很好的办法。

## 四、其他的集合类

### 1、LinkedHashMap

`可以让key保持一定顺序的Map`

在原来的Map基础上维护了插入顺序的一个双向链表

![image-20210719162005725](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9B%86%E5%90%88.assets/image-20210719162005725.png)



```java
public static void main(String[] args) {
    Map<String, String> linkedHashMap = new LinkedHashMap<>(16);
    linkedHashMap.put("a", "123");
    linkedHashMap.put("b", "123");
    linkedHashMap.put("c", "123");
    linkedHashMap.put("d", "123");
    System.out.println(linkedHashMap);
}

```

#### 2、使用LinkedHashMap实现LRU算法

- LRU：Least Recently Used—最近最少被访问的，然后干掉
- 本机就是远端服务器的缓存，内存比磁盘更近，内存就是磁盘的缓存，LinkedHashMap和HashMap都是把数据保存在内存中的，User、Teacher都是存数据的，集合就是把User归置起来，存放一堆的User
- 就是删除掉本机中很少使用的东西，然后腾出空间，以后需要使用的时候去服务器中找
- 默认是关闭访问的，如果打开访问，传入参数true，输出的时候，被访问过的数据就会在最后

```java
//判断first是不是空，，根据是否查看过决定要不要删除这个值
if (evict && (first = head) != null && removeEldestEntry(first)) {
    K key = first.key;
    removeNode(hash(key), key, null, false, true);
}

```

```java
package com.ydlclass;

import java.util.LinkedHashMap;
import java.util.Map;

public class LRU<K, V> extends LinkedHashMap<K, V> {
    //构造器都是重写的父类的构造器，定义了一个私有的最大容量，重写了删除元素的方法，如果大于最大容量，就删除不经常访问的元素
    private int max_access = 5;
    public LRU(int initialCapacity, int max_access) {
        super(initialCapacity, 0.75F, true);
        this.max_access = max_access;
    }
    public LRU() {
        super(16, 0.75F, true);
        max_access = 5;
    }

    @Override
    //大于3就返回true，集合中只能有三个元素，如果大于就自动删除
    protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
        return size() > max_access;
    }

    public static void main(String[] args) {

    }
}

```

### 2、TreeMap

```java
public static void main(String[] args) {
        /**
         * TreeMap中有实现的Comparable接口，就可以按照传入的key进行比较，如果子类有实现的比较方法就使用子类的比较方法，
         * 如果没有就把key强转成Comparator，使用他的比较方法
         * 一般使用的方法是传入一个比较器
         */

        TreeMap<Integer, String> treeMap = new TreeMap<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o1 - o2      ;
            }
        });

    }

```

### 3、Collections工具类

```java
public static void main(String[] args) {
    List<Integer> nums = new ArrayList<>();
    //添加List
    Collections.addAll(nums, 1, 2, 3, 4, 5, 6, 7);
    //打乱List——一副扑克
    Collections.shuffle(nums);
    //Arrays工具，返回值是一个Integer，并不是ArrayList
    List<Integer> integers = Arrays.asList(1, 2, 3, 4, 5, 6);
    System.out.println(integers);
    System.out.println(nums);
}

```



## 五、并发修改异常

### 1、并发修改异常

多个线程进行`删除操作`会出现这种错误

在多个线程进行操作的时候，会出现数组下标越界，然后new一个并发修改异常—`源码`先进入iterator的构造器，然后进入子类ArrayList，然后查看Itr中的remove方法，还有上面的checkForComodification()，有两个参数，一个实际修改次数，一个期望修改次数，每一个iterator都有一个期望修改，实际修改在List集合上(`共享数据`)，本质还是调用的是arrayList的remove方法，每次删除都会把实际修改次数+1，涉及到多个线程共享数据的时候就会涉及到线程安全的问题(可见性、原子性、有序性)，多个线程操作的时候会影响共享数据的值，但是某个线程中的iterator中的期望修改就会和实际修改次数不同，就会出现并发修改异常——`s涉及到cas—线程-三-10-(3)cas`

```java
public static void main(String[] args) {
    test();

}
public static void test(){
    List<Integer> nums = new ArrayList<>();
    for (int i = 0; i < 100000; i++) {
        nums.add(new Random().nextInt(100000));
    }
    for (int i = 0; i < 20; i++) {
        new Thread(()->{
            Iterator<Integer> iterator = nums.iterator();
            while (iterator.hasNext()){
                Integer next = iterator.next();
                if (next > 10000)
                    iterator.remove();
            }
        }).start();
    }
}

```

### 2、面试会问的线程安全的集合类(不使用了)

List原来是安全的，但是如果多个线程对数据进行操作的时候就会出现异常的可能，是多个线程对共享数据进行操作的时候会出现异常。

线程安全的类：HashTable(Map)、Vector(List)，因为类中的方法都是用`synchronized`修饰的，但是已经很久不更新了，所以我们不使用。

```java
List<Integer> list = new Vector<>();//父类引用指向子类对象

```

```java
Map<Integer, String> map = new Hashtable<>();

```

​	这两个类，其实很久没更新了，但是还是有面试会问，其实这两个类都有历史渊源，最开始就是在ArrayList和HashMap的基础上增加了Syncronized，但是后来ArrayList和hashMap一直在改进，这两个就成了历史了，反而现在问它们的区别其实意义不大了。

> HashMap和HashTable区别

1. HashMap允许将 null 作为一个 entry 的 key 或者 value，而 Hashtable 不允许。
2. HashMap 把 Hashtable 的 contains 方法去掉了，改成 containsValue 和 containsKey。因为 contains 方法容易让人引起误解。
3. HashTable 继承自 Dictionary 类，而 HashMap 是 Java1.2 引进的 Map interface 的一个实现。
4. HashTable 的方法是 Synchronized修饰 的，而 HashMap 不是，这也是是否能保证线程安全的重要保障。
5. Hashtable 和 HashMap 采用的 hash/rehash 算法都不一样。
6. 获取数组下标的算法不同，



> ArrayList和Vector的区别

1. Vector是多线程安全的，线程安全就是说多线程访问同一代码，不会产生不确定的结果。而ArrayList不是，这个可以从源码中看出，Vector类中的方法很多，有synchronized进行修饰，这样就导致了Vector在效率上无法与ArrayList相比；
2. 两个都是采用线性连续空间存储元素，但是当空间不足的时候，两个类的扩容方式是不同的。
3. Vector是一种老的动态数组，是线程同步的，效率很低，一般不赞成使用。

### 3、现在经常使用的线程安全集合类

#### (1)CopyOnWriteList(写时复制的List)

在修改List的时候，复制一份；给写请求上锁，请求就会排队，`ReentrantLock`，复制一份旧数组，然后进行写操作，最后改变引用，原来的空间就会被JVM垃圾回收器回收。

`CopyOnWriteList的源码——自行查看`

```java
public boolean add(E e) {
    final ReentrantLock lock = this.lock;//可重入锁
    lock.lock();//上锁
    try {
        // 复制一个新的数组，在新的独立空间进行添加操作
        Object[] elements = getArray();
        int len = elements.length;
        Object[] newElements = Arrays.copyOf(elements, len + 1);
        newElements[len] = e;
        // 修改引用
        setArray(newElements);
        return true;
    } finally {
        //解锁
        lock.unlock();
    }
}


final void setArray(Object[] a) {
    array = a;
}

```

#### (2)ConcurrentHashMap—重要且难—表头锁

多个线程对同一个数据链(一溜灯笼)的同一个位置进行操作的时候可能会造成数据丢失，`解决方法`：使用表头当锁，表头是一个对象，其中有对象头，对象头中有锁信息，线程进来的时候只锁一列

1.7：每次扩容的时候都会打乱顺序，改变热点数据的顺序，所以还不如改成尾插，降低复杂度

1.8中的ConcurrentHashMap和HashMap的代码基本一样，只不过在有些操作上使用了cas，有些地方加了锁。

```java
public class ConcurrentHashMap<K,V> extends AbstractMap<K,V>
    implements ConcurrentMap<K,V>, Serializable {

```



构造器：

```java
public ConcurrentHashMap(int initialCapacity) {
    if (initialCapacity < 0)
        throw new IllegalArgumentException();
    int cap = ((initialCapacity >= (MAXIMUM_CAPACITY >>> 1)) ?
               MAXIMUM_CAPACITY :
               tableSizeFor(initialCapacity + (initialCapacity >>> 1) + 1));
    this.sizeCtl = cap;
}

```

我们简单看看putVal算法

```java
final V putVal(K key, V value, boolean onlyIfAbsent) {
    if (key == null || value == null) throw new NullPointerException();
    // 计算hash
    int hash = spread(key.hashCode());
    int binCount = 0;
    for (Node<K,V>[] tab = table;;) {
        Node<K,V> f; int n, i, fh;
        // 如果没有hash表，就创建一个
        if (tab == null || (n = tab.length) == 0)
            tab = initTable();
        // 给f赋值就是hash表中的元素
        else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {
            // 这里也是线程安全的
            // 如果没有就使用cas的方式添加
            if (casTabAt(tab, i, null,
                         new Node<K,V>(hash, key, value, null)))
                break;                   // no lock when adding to empty bin
        }
        else if ((fh = f.hash) == MOVED)
            tab = helpTransfer(tab, f);
        else {
            V oldVal = null;
            // 看这是关键，这加了锁，f是什么啊？
            // f是头节点
            synchronized (f) {
                if (tabAt(tab, i) == f) {
                    if (fh >= 0) {
                        binCount = 1;
                        for (Node<K,V> e = f;; ++binCount) {
                            K ek;
                            if (e.hash == hash &&
                                ((ek = e.key) == key ||
                                 (ek != null && key.equals(ek)))) {
                                oldVal = e.val;
                                if (!onlyIfAbsent)
                                    e.val = value;
                                break;
                            }
                            Node<K,V> pred = e;
                            if ((e = e.next) == null) {
                                pred.next = new Node<K,V>(hash, key,
                                                          value, null);
                                break;
                            }
                        }
                    }
                    else if (f instanceof TreeBin) {
                        Node<K,V> p;
                        binCount = 2;
                        if ((p = ((TreeBin<K,V>)f).putTreeVal(hash, key,
                                                              value)) != null) {
                            oldVal = p.val;
                            if (!onlyIfAbsent)
                                p.val = value;
                        }
                    }
                }
            }
            if (binCount != 0) {
                if (binCount >= TREEIFY_THRESHOLD)
                    treeifyBin(tab, i);
                if (oldVal != null)
                    return oldVal;
                break;
            }
        }
    }
    addCount(1L, binCount);
    return null;
}

```



其实，面试很喜欢问1.7和1.8的区别

主要是1.7的分段锁是一个很经典的案例，造成这个的原因还有一个更重要的就是`JDK1.7使用的是头插，而1.8改成尾插`

我们简单的看一下1.7的put方法实现：

```java
public V put(K key, V value) {
    if (key == null)
        return putForNullKey(value);
    int hash = hash(key);
    int i = indexFor(hash, table.length);
    // 找到相同的key，覆盖
    for (Entry<K,V> e = table[i]; e != null; e = e.next) {
        Object k;
        if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
            V oldValue = e.value;
            e.value = value;
            e.recordAccess(this);
            return oldValue;
        }
    }

    modCount++;
    // 否则就是新增
    addEntry(hash, key, value, i);
    return null;
}


void addEntry(int hash, K key, V value, int bucketIndex) {
    // 判断是否需要扩容
    if ((size >= threshold) && (null != table[bucketIndex])) {
        resize(2 * table.length);
        hash = (null != key) ? hash(key) : 0;
        bucketIndex = indexFor(hash, table.length);
    }
	// 创建
    createEntry(hash, key, value, bucketIndex);
}

void createEntry(int hash, K key, V value, int bucketIndex) {
    Entry<K,V> e = table[bucketIndex];
    // 头插啊
    table[bucketIndex] = new Entry<>(hash, key, value, e);
    size++;
}

// 1.7中居然直接就是Entry不是node
Entry(int h, K k, V v, Entry<K,V> n) {
    value = v;
    next = n;
    key = k;
    hash = h;
}
    

```



#### JDK8以前是头插法，JDK8后是尾插法，那为什么要从头插法改成尾插法？

1. 因为头插法会造成循环链表
2. JDK7用头插是考虑到了一个所谓的热点数据的点(新插入的数据可能会更早用到)，但这其实是个伪命题,因为JDK7中rehash的时候，旧链表迁移新链表的时候，如果在新表的数组索引位置相同，则链表元素会倒置(就是因为头插)， 所以最后的结果 还是打乱了插入的顺序 ，所以总的来看支撑JDK7使用头插的这点原因也不足以支撑下去了 ，所以就干脆换成尾插 一举多得。



#### 多线程并发的情况下为什么会产生循环链表？

1. 使用的是jdk1.7；
2. 必须有线程争抢；
3. 必须咋线程争抢的时候使用扩容的方法；

扩容的时候数组的长度会发生改变，所有的元素的hash值都会重新计算

两个线程同时扩容，由于线程1已经扩容完毕，把变量刷回主存，但是线程2还在扩容，此时主存中的指向已经改变，就会形成`循环链表`。(因为1.7是头插法，每次扩容都会改变链表的顺序，指针倒换)



#### 1.7的加锁实现(分段锁)

`调用整体的put方法，首先会进行选择，根据key看是在哪个segment中，然后调用segments中的put方法，segment继承了锁类，就有加锁、得到锁的方法，就会一直使用获得锁的方法，直至获得锁，然后添加值。`

```
/**
* Mask value for indexing into segments. The upper bits of a
* key's hash code are used to choose the segment.
*/
final int segmentMask;

/**
* Shift value for indexing within segments.
*/
final int segmentShift;

/**
* The segments, each of which is a specialized hash table.
*/
final Segment<K,V>[] segments;

transient Set<K> keySet;
transient Set<Map.Entry<K,V>> entrySet;
transient Collection<V> values;

```





```java
static final class Segment<K,V> extends ReentrantLock implements Serializable {

    private static final long serialVersionUID = 2249069246763182397L;

    static final int MAX_SCAN_RETRIES =
        Runtime.getRuntime().availableProcessors() > 1 ? 64 : 1;
        
	// 我们陡然发现每一个分段里边保存了一个数组，这不就是数组套数组吗？
    transient volatile HashEntry<K,V>[] table;

    transient int count;

    final float loadFactor;

```





```java
@SuppressWarnings("unchecked")
public ConcurrentHashMap(int initialCapacity,
                         float loadFactor, int concurrencyLevel) {
    if (!(loadFactor > 0) || initialCapacity < 0 || concurrencyLevel <= 0)
        throw new IllegalArgumentException();
    if (concurrencyLevel > MAX_SEGMENTS)
        concurrencyLevel = MAX_SEGMENTS;
    // Find power-of-two sizes best matching arguments
    int sshift = 0;
    int ssize = 1;
    while (ssize < concurrencyLevel) {
        ++sshift;
        ssize <<= 1;
    }
    this.segmentShift = 32 - sshift;
    this.segmentMask = ssize - 1;
    if (initialCapacity > MAXIMUM_CAPACITY)
        initialCapacity = MAXIMUM_CAPACITY;
    int c = initialCapacity / ssize;
    if (c * ssize < initialCapacity)
        ++c;
    int cap = MIN_SEGMENT_TABLE_CAPACITY;
    while (cap < c)
        cap <<= 1;
    // create segments and segments[0]
    Segment<K,V> s0 =
        new Segment<K,V>(loadFactor, (int)(cap * loadFactor),
                         (HashEntry<K,V>[])new HashEntry[cap]);
    Segment<K,V>[] ss = (Segment<K,V>[])new Segment[ssize];
    UNSAFE.putOrderedObject(ss, SBASE, s0); // ordered write of segments[0]
    this.segments = ss;
}

```



```java
public V put(K key, V value) {
    Segment<K,V> s;
    if (value == null)
        throw new NullPointerException();
    int hash = hash(key);
    int j = (hash >>> segmentShift) & segmentMask;
    if ((s = (Segment<K,V>)UNSAFE.getObject          // nonvolatile; recheck
         (segments, (j << SSHIFT) + SBASE)) == null) //  in ensureSegment
        s = ensureSegment(j);
    return s.put(key, hash, value, false);
}

```





```java
final V put(K key, int hash, V value, boolean onlyIfAbsent) {
    // 先尝试加锁，加不上再疯狂加锁，反正能加上锁，他继承了ReentrantLock
    HashEntry<K,V> node = tryLock() ? null :
    scanAndLockForPut(key, hash, value);
    V oldValue;
    try {
        HashEntry<K,V>[] tab = table;
        int index = (tab.length - 1) & hash;
        HashEntry<K,V> first = entryAt(tab, index);
        for (HashEntry<K,V> e = first;;) {
            if (e != null) {
                K k;
                if ((k = e.key) == key ||
                    (e.hash == hash && key.equals(k))) {
                    oldValue = e.value;
                    if (!onlyIfAbsent) {
                        e.value = value;
                        ++modCount;
                    }
                    break;
                }
                e = e.next;
            }
            else {
                if (node != null)
                    node.setNext(first);
                else
                    node = new HashEntry<K,V>(hash, key, value, first);
                int c = count + 1;
                if (c > threshold && tab.length < MAXIMUM_CAPACITY)
                    rehash(node);
                else
                    setEntryAt(tab, index, node);
                ++modCount;
                count = c;
                oldValue = null;
                break;
            }
        }
    } finally {
        unlock();
    }
    return oldValue;
}

```



```java
private HashEntry<K,V> scanAndLockForPut(K key, int hash, V value) {
    HashEntry<K,V> first = entryForHash(this, hash);
    HashEntry<K,V> e = first;
    HashEntry<K,V> node = null;
    int retries = -1; // negative while locating node
    // 不定的重新抢锁，抢锁的过程当中完成很多初始化的工作
    
    while (!tryLock()) {
        HashEntry<K,V> f; // to recheck first below
        // 第一次再次抢锁时顺便初始化了entry
        if (retries < 0) {
            if (e == null) {
                if (node == null) // speculatively create node
                    node = new HashEntry<K,V>(hash, key, value, null);
                retries = 0;
            }
            // 发现重复的key就不用初识化entry了
            else if (key.equals(e.key))
                retries = 0;
            else
                e = e.next;
        }
        // 如果超过最大的抢锁的次数直接调用lock
        else if (++retries > MAX_SCAN_RETRIES) {
            lock();
            break;
        }
        else if ((retries & 1) == 0 &&
                 (f = entryForHash(this, hash)) != first) {
            e = first = f; // re-traverse if entry changed
            retries = -1;
        }
    }
    return node;
}

```

### (3)guava提供的不可变集合

对于线程安全，最好的方法是使Map不可变

`引入guava包`

```java
public static void main(String[] args) {
        Integer[] nums = {1, 2, 3, 4};
        ImmutableList<Integer> list = ImmutableList.copyOf(nums);
        System.out.println(list);
  		ImmutableMultimap<String, Integer> map = ImmutableMultimap.of("a", 1, "b", 2);
        System.out.println(map);
    }

```



## 六、JUnit单元测试

### 1、Junit入门

> JUnit 是一个 Java 编程语言的单元测试框架。JUnit 在测试驱动的开发方面有很重要的发展，是起源于 JUnit 的一个统称为 xUnit 的单元测试框架之一。

> JUnit的好处：

1. 可以书写一系列的测试方法，对项目所有的接口或者方法进行单元测试。
2. 启动后，自动化测试，并判断执行结果, 不需要人为的干预。
3. 只需要查看最后结果，就知道整个项目的方法接口是否通畅。
4. 每个单元测试用例相对独立，由Junit 启动，自动调用。不需要添加额外的调用语句。
5. 添加，删除，屏蔽测试方法，不影响其他的测试方法。 开源框架都对JUnit 有相应的支持。

JUnit其实就是一个jar包，idea中可以通过自动修复功能直接添加。但是为了演示清楚，我们还是安装规矩引入jar包完成。

使用JUnit我们需要引入下边两个jar包即可：

1. hamcrest-core-1.1.jar
2. junit-4.12.jar

网站有提供。

加入JUnit后，我们可以创建测试类，测试方法，每一个测试方法都可以独立运行：

![1659537303574](%E5%9B%BE%E7%89%87/1659537303574.png)



### 2、JUnit 断言

断定最后出现的结果是不是预期的结果。

Junit所有的断言都包含在 Assert 类中。

这个类提供了很多有用的断言方法来编写测试用例。只有失败的断言才会被记录。Assert 类中的一些有用的方法列式如下：

1. `void assertEquals(boolean expected, boolean actual)`:检查两个变量或者等式是否平衡
2. `void assertTrue(boolean expected, boolean actual)`:检查条件为真
3. `void assertFalse(boolean condition)`:检查条件为假
4. `void assertNotNull(Object object)`:检查对象不为空
5. `void assertNull(Object object)`:检查对象为空
6. `void assertSame(boolean condition)`:assertSame() 方法检查两个相关对象是否指向同一个对象
7. `void assertNotSame(boolean condition)`:assertNotSame() 方法检查两个相关对象是否不指向同一个对象
8. `void assertArrayEquals(expectedArray, resultArray)`:assertArrayEquals() 方法检查两个数组是否相等

![image-20210908232010018](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9B%86%E5%90%88.assets/image-20210908232010018.png)



### 3、JUbit注解

1. `Test`:这个注释说明依附在 JUnit 的 public void 方法可以作为一个测试案例。
2. `Before`:有些测试在运行前需要创造几个相似的对象。在 public void 方法加该注释是因为该方法需要在 test 方法前运行。
3. `After`:如果你将外部资源在 Before 方法中分配，那么你需要在测试运行后释放他们。在 public void 方法加该注释是因为该方法需要在 test 方法后运行。

`可以有多个Before、After`

```java
package com.ydlclass;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

public class JunitTest {
    @Before
    public void beforeTest(){
        System.out.println("before");
    }
    @Before
    public void beforeTest2(){
        System.out.println("before2");
    }
    @Test
    public void testOne(){
        System.out.println("testOne");
    }
    @Test
    public void testTwo(){
        System.out.println("testTwo");
    }
    @After
    public void afterTest(){
        System.out.println("after");
    }
    @After
    public void afterTest2(){
        System.out.println("after2");
    }
}


```

### 4、命名规范

单元测试类的命名规范：被测试类的类名+Test

单元测试类中测试方法的命名规范为：test+被测试方法的名字+XXX，其中XXX为对同一个方法的不同的单元测试用例的自定义名称。

```java
public class OrderTest {
    Order order = new Order();
    @Test
    public void testFun1(){
        order.fun1();
    }
}

```



## 七、性能对比

### 1、HashTable和ConcurrentHashMap

```java
@Test
public void testHash() throws InterruptedException {
    final Map<Integer, Integer> hashTableMap = new Hashtable<>(5000000);
    final CountDownLatch countDownLatch = new CountDownLatch(50);
    long start = System.currentTimeMillis();
    for (int i = 0; i < 50; i++) {
        new Thread(()->{
            for (int j = 0; j < 100000; j++) {
                hashTableMap.put(1, 1);
            }
            countDownLatch.countDown();
        }).start();
    }
    countDownLatch.await();
    long end = System.currentTimeMillis();
    System.out.println("HashTable" + (end - start));

    //因为ConcurrentHashMap是锁表头的，不会出现hash碰撞，瞬间就放进去了，线程不会阻塞
    System.out.println("开始测试第二个");
    final Map<Integer, Integer> map2 = new ConcurrentHashMap<>(5000000);
    start = System.currentTimeMillis();
    for (int i = 0; i < 50; i++) {
        new Thread(()->{
            for (int j = 0; j < 100000; j++) {
                map2.put(1, 1);
            }
            countDownLatch.countDown();
        }).start();
    }
    countDownLatch.await();
    end = System.currentTimeMillis();
    System.out.println("concurrentHashMap" + (end-start));
}

```

### 2、ArrayList和LinkedList

`工作使用ArrayList的很多，经常在尾部操作数据，随即位置操作数据也有，在过滤数据的时候使用LinkedList`

对于链表来说，添加数据的时候使用头插和尾插，速度是近似的，因为都是改变的引用指向

对于数组来说，头插法比尾插法慢很多，因为头插法要挪动数据，尾插法比较起来是数组比较快

遍历List集合，不论是是用for循环还是迭代器，都是ArrayList快

进行删除的时候，LinkedList比ArrayList快，因为数组要进行移动—删除之后进行移动，但是进行尾删的时候，数组就快

#### （1）顺序添加

```java
@Test
public void testArrayListAdd(){
    List<Integer> list = new ArrayList<>();
    Long start = System.currentTimeMillis();
    for (int i = 0; i < 10000000; i++) {
        list.add((int)(Math.random()*100));
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    用时243毫秒。

@Test
public void testLinkedListAdd(){
    List<Integer> list = new LinkedList<>();
    Long start = System.currentTimeMillis();
    for (int i = 0; i < 10000000; i++) {
        list.add((int)(Math.random()*100));
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    用时2524毫秒。

```

#### （2）使用for循环迭代获取

```java
@Test
public void testArrayListFor(){
    List<Integer> list = new ArrayList<>();
    for (int i = 0; i < 10000000; i++) {
        list.add((int)(Math.random()*100));
    }
    System.out.println("开始------");
    Long start = System.currentTimeMillis();
    for (int i = 0; i < list.size(); i++) {
        list.get(i);
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    用时2毫秒。

@Test
public void testLinkedListFor(){
    List<Integer> list = new LinkedList<>();
    for (int i = 0; i < 10000000; i++) {
        list.add((int)(Math.random()*100));
    }
    System.out.println("开始------");
    Long start = System.currentTimeMillis();
    for (int i = 0; i < list.size(); i++) {
        list.get(i);
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    无法计算时间。

```

#### （3）使用迭代器迭代获取

```java
@Test
public void testArrayListIterator(){
    List<Integer> list = new ArrayList<>();
    for (int i = 0; i < 10000000; i++) {
        list.add((int)(Math.random()*100));
    }
    System.out.println("开始------");
    Long start = System.currentTimeMillis();
    Iterator<Integer> iterator = list.iterator();
    while (iterator.hasNext()){
        iterator.next();
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    开始------
	用时4毫秒。

@Test
public void testLinkedListIterator(){
    List<Integer> list = new LinkedList<>();
    for (int i = 0; i < 10000000; i++) {
        list.add((int)(Math.random()*100));
    }
    System.out.println("开始------");
    Long start = System.currentTimeMillis();
    Iterator<Integer> iterator = list.iterator();
    while (iterator.hasNext()){
        iterator.next();
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}

结果：
    开始------
	用时42毫秒。

```

#### （4）头插

```java
@Test
public void testArrayListAddHeader(){
    List<Integer> list = new ArrayList<>();
    Long start = System.currentTimeMillis();
    for (int i = 0; i < 10000000; i++) {
        list.add(0,(int)(Math.random()*100));
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    无法算出，太慢

@Test
public void testLinkedListAddHeader(){
    List<Integer> list = new LinkedList<>();
    Long start = System.currentTimeMillis();
    for (int i = 0; i < 10000000; i++) {
        list.add(0,(int)(Math.random()*100));
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    用时2487毫秒。

```

#### （5）随机删除

```java
@Test
public void testLinkedListDel(){
    List<Integer> list = new LinkedList<>();
    for (int i = 0; i < 10000000; i++) {
        list.add(0,(int)(Math.random()*100));
    }
    Long start = System.currentTimeMillis();
    // 不用管为啥，这就是排序，复制过来用就行，写个冒泡也行
    Iterator<Integer> iterator = list.iterator();
    while (iterator.hasNext()){
        if(iterator.next()>5000000){
            iterator.remove();
        }
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    用时45毫秒。

@Test
public void testArrayListDel(){
    List<Integer> list = new ArrayList<>();
    for (int i = 0; i < 10000000; i++) {
        list.add(0,(int)(Math.random()*100));
    }
    Long start = System.currentTimeMillis();
    // 不用管为啥，这就是排序，复制过来用就行，写个冒泡也行
    Iterator<Integer> iterator = list.iterator();
    while (iterator.hasNext()){
        if(iterator.next()>5000000){
            iterator.remove();
        }
    }
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    太慢，时间没出来

```



#### （6）自带的排序方法

排序比较耗费资源，所以我们把量级调整到了十万。

```java
@Test
public void testArrayListSort(){
    List<Integer> list = new ArrayList<>();
    for (int i = 0; i < 100000; i++) {
        list.add(0,(int)(Math.random()*100));
    }
    Long start = System.currentTimeMillis();
    // 不用管为啥，这就是排序，复制过来用就行，写个冒泡也行
    list.sort(Comparator.comparingInt(num -> num));
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}
结果：
    用时49毫秒。

@Test
public void testLinkedListSort(){
    List<Integer> list = new LinkedList<>();
    for (int i = 0; i < 100000; i++) {
        list.add(0,(int)(Math.random()*100));
    }
    Long start = System.currentTimeMillis();
    // 不用管为啥，这就是排序，复制过来用就行，写个冒泡也行
    list.sort(Comparator.comparingInt(num -> num));
    Long end = System.currentTimeMillis();
    System.out.printf("用时%d毫秒。",end-start);
}

结果：
    用时53毫秒。

```

#### （7）思考

其实我们学习时，总是去背诵概念：

数组查询快，插入慢。链表插入慢，查询快。

- 但是经过测试，尾插反而是数组快，而尾插的使用场景极多。
- 测试了各种迭代，遍历方法，ArrayList基本都是比LinkedList要快。
- 随机插入，链表会快很多，确实有一些特殊的场景LinkedList更合适，比如以后我们学的过滤器链。
- 随机删除，链表的效率也是无比优于数组，如果我们存在需要过滤删除大量随机元素的场景也能使用linkedlist。
- 我们工作中的使用还是以ArrayList为主，因为它的使用场景最多。



## 八、Java8特性

### 1、接口默认方法

某个接口会被大量的子类实现，如果每个子类都要重构接口的方法，这种重构的代价是很大的，所以会在接口中添加了默认方法，子类会继承接口的默认方法，防止重写一个接口的时候，就要重写实现他的所有的子类。——`其实是一种偷懒的方法`



### 2、函数式接口

函数式接口规定了一个接口有且仅有一个抽象方法。

静态方法、静态类本身不是属于实例对象的，不需要i构造，任何的类中都可以有，如果是静态的，可以删除psf——interface中 默认的就是静态的。

`@FunctionalInterface`函数式接口的注解这个接口有点像函数，在面向对象的语言中，方法不是一等公民，不可以直接调用，只能通过new一个实例对象载体来调用。在Java中送礼物必须要封装`(面向对象的特性)`，但是有的语言就可以直接把函数当成一个参数传递给另外一个函数`(高阶函数)`，传递的是一种行为，而不是一个具体的实例对象，然后就产生了`函数式接口`，只有一个抽象方法，把这个接口的实现类传进去，就相当于把这个方法传进去了，本质上传的还是一个类。

```java
new Thread(()->{});

```

接下来给大家介绍几个常用的函数式接口，在我们接下来要学习的Lamdba表达式中大量使用。

一个函数式接口只能有一个抽象方法，这个抽象方法就代表了这个类具有的能力，所以使用匿名内部类实现函数式接口就有很多的重复代码，就产生了箭头函数。

> - 因为只有一个抽象方法，所以方法名可以省略；
> - 参数类型可以省略；
> - 只有一个参数，()可以省略；
> - 参数后面加`->`箭头后面跟着大括号，大括号中是具体的方法体；
> - 如果方法体中只有一行代码，可以省略大括号；
> - 如果一行代码而且还是return，return都可以省略；
> - 如果只有一个参数而且还是输出这个参数`System.out::println;`，可以等号右边只写这个；
> - 小括号只能在只有一个参数的时候省略。

> 消费者，消费数据
>
> ​		——能吃掉数据，但是吐不出来。(有接收值，但是没有返回值)

```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}

```

> 供应商，给我们产生数据
>
> ​		——没有参数，但是有返回值

```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}

```

> 断言，判断传入的t是不是满足条件
>
> ​		——返回的就是一个true和false

```java
@FunctionalInterface
public interface Predicate<T> {

    boolean test(T t);
}

```

> 函数，就是将一个数据转化成另一个数据

```java
@FunctionalInterface
public interface Function<T, R> {
    R apply(T t);
}

```



​		我们在思考上边的代码的时候，不要胡思乱想，它们就是一组接口，和我们的普通接口一样，每个接口代表一种能力，需要子类去实现，因为它们是函数式接口，所以匿名内部类都可以写成箭头函数的形式。

### 3、Optional

#### （1）简介

 		 Optional类是Java8为了解决null值判断问题，借鉴google guava类库的Optional类而引入的一个同名Optional类，使用Optional类可以避免显式的null值判断（null的防御性检查），避免null导致的NPE（NullPointerException）。



#### （2）Optional对象的创建

  Optional类提供了三个静态方法empty()、of(T value)、ofNullable(T value)来创建Optinal对象，示例如下：

```dart
// 1、创建一个包装对象值为空的Optional对象
Optional<String> optStr = Optional.empty();
// 2、创建包装对象值非空的Optional对象
Optional<String> optStr1 = Optional.of("optional");
// 3、创建包装对象值允许为空的Optional对象
Optional<String> optStr2 = Optional.ofNullable(null);

```



#### （3）Optional 类典型接口的使用

下面以一些典型场景为例，列出Optional API常用接口的用法，并附上相应代码。

> get()方法

   简单看下get()方法的源码：

```csharp
public T get() {
    if (value == null) {
        throw new NoSuchElementException("No value present");
    }
    return value;
}

```

可以看到，get()方法主要用于返回包装对象的实际值，但是如果包装对象值为null，会抛出NoSuchElementException异常。



> isPresent()方法

   isPresent()方法的源码：

```csharp
public boolean isPresent() {
    return value != null;
}

```

可以看到，isPresent()方法用于判断包装对象的值是否非空。下面我们来看一段糟糕的代码：

```csharp
public static String getGender(Student student){
    Optional<Student> stuOpt =  Optional.ofNullable(student);
    if(stuOpt.isPresent())
    {
        return stuOpt.get().getGender();
    }

    return "Unkown";
}

```

这段代码实现的是第一章(简介)中的逻辑，但是**这种用法不但没有减少null的防御性检查，而且增加了Optional包装的过程，违背了Optional设计的初衷，因此开发中要避免这种糟糕的使用**



> ifPresent()方法

   ifPresent()方法的源码：



```csharp
public void ifPresent(Consumer<? super T> consumer) {
    if (value != null)
        consumer.accept(value);
}

```

ifPresent()方法接受一个Consumer对象（消费函数），如果包装对象的值非空，运行Consumer对象的accept()方法。示例如下：

```csharp
/**
* 如果存在就要传入一个消费者
*/
optional.ifPresent(u -> System.out.println("user = " + u));

```

上述示例用于打印学生姓名，由于ifPresent()方法内部做了null值检查，调用前无需担心NPE问题。



> orElse()方法

 orElse()方法的源码：

```csharp
public T orElse(T other) {
    return value != null ? value : other;
}

```

orElse()方法功能比较简单，即如果包装对象值非空，返回包装对象值，否则返回入参other的值（默认值）。

```cpp
/**
* 如果为空，给一个默认选项
*/
User user1 = optional.orElse(new User("默认用户", 002));
System.out.println(user1.getName());

```



> orElseGet()方法

   orElseGet()方法的源码：



```csharp
    public T orElseGet(Supplier<? extends T> other) {
        return value != null ? value : other.get();
    }

```

orElseGet()方法与orElse()方法类似，区别在于orElseGet()方法的入参为一个Supplier对象，用Supplier对象的get()方法的返回值作为默认值。如：

```java
/**
*如果没有就new一个空的
*/
User user1 = optional.orElseGet(User::new);
System.out.println(user1);

```



> orElseThrow()方法

   orElseThrow()方法的源码：

```csharp
public <X extends Throwable> T orElseThrow(Supplier<? extends X> exceptionSupplier) throws X {
    if (value != null) {
        return value;
    } else {
        throw exceptionSupplier.get();
    }
}

```

​		orElseThrow()方法其实与orElseGet()方法非常相似了，入参都是Supplier对象，只不过orElseThrow()的Supplier对象必须返回一个Throwable异常，并在orElseThrow()中将异常抛出：



```cpp
/**
* 如果没有就new一个异常，异常继承Throwable
* 直接返回一个new异常，最后运行框就是运行时异常
*/
optional.orElseThrow(()-> new RuntimeException("你的User是空"));

```

orElseThrow()方法适用于包装对象值为空时需要抛出特定异常的场景。

## 九、Stream编程

Java8中的Stream是对容器对象功能的增强，它专注于对容器对象进行各种非常便利、高效的 聚合操作（aggregate operation），或者大批量数据操作 (bulk data operation)。Stream API借助于同样新出现的Lambda表达式，极大的提高编程效率和程序可读性。同时，它提供`串行(单线程)`和`并行(多线程)`两种模式进行汇聚操作，并发模式能够充分利用多核处理器的优势。通常，编写并行代码很难而且容易出错, 但使用Stream API无需编写一行多线程的代码，就可以很方便地写出高性能的并发程序。

​		我觉得我们可以将流看做流水线，这个流水线是处理数据的流水线，一个产品经过流水线会有一道道的工序就如同对数据的中间操作，比如过滤我不需要的，给数据排序能，最后的终止操作就是产品从流水线下来，我们就可以统一打包放入仓库了。

​		当我们使用一个流的时候，通常包括三个基本步骤：获取一个数据源（source）→ 数据转换 → 执行操作获取想要的结果。**每次转换原有Stream对象不改变，返回一个新的Stream对象（可以有多次转换）**，这就允许对其操作可以像链条一样排列，变成一个管道，如下图所示:

Stream有几个特性：

1. Stream不存储数据，而是按照特定的规则对数据进行计算，一般会输出结果。
2. Stream不会改变数据源，通常情况下会产生一个新的集合或一个值。
3. Stream具有延迟执行特性，只有调用终端操作时，中间操作才会执行。`懒汉`，结果在终端操作上

![image-20210908180935125](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E9%9B%86%E5%90%88.assets/image-20210908180935125.png)

### 1、创建流

```java
@Test
    public void creatTest(){
        
        //通过集合创建Stream
        List<Integer> list = new ArrayList<>();
        Stream<Integer> stream = list.stream();
        
        //使用数组进行创建
        Integer[] nums = {1, 2, 3, 4};
        Stream<Integer> stream1 = Arrays.stream(nums);
        
        //使用Stream的静态方法
        Stream<Integer> concat = Stream.concat(stream, stream1);//合并
        Stream<Integer> integerStream = Stream.of(1, 2, 3);//of传入可变参数
        
        //使用Random生成随机数流
        IntStream ints = new Random().ints(10);

    }

```

### 2、Stream的终端操作

#### (0)准备操作

```java
public class Person {
    private String name;  // 姓名
    private int salary; // 薪资
    private int age; // 年龄
    private String sex; //性别
    private String area;  // 地区

    public Person() {
    }

    public Person(String name, int salary, int age, String sex, String area) {
        this.name = name;
        this.salary = salary;
        this.age = age;
        this.sex = sex;
        this.area = area;
    }
}

```



#### (1)遍历/匹配(foreach/find/match)

```java
@Test
public void foreachTest(){
    // 打印集合的元素
    simpleList.stream().forEach(System.out::println);
    // 其实可以简化操作的
    simpleList.forEach(System.out::println);
}


@Test
public void findTest(){
    // 找到第一个
    Optional<Integer> first = simpleList.stream().findFirst();
    // 随便找一个,可以看到findAny()操作，返回的元素是不确定的，
    // 对于同一个列表多次调用findAny()有可能会返回不同的值。
    // 使用findAny()是为了更高效的性能。如果是数据较少，串行地情况下，一般会返回第一个结果，
    // 如果是并行的情况，那就不能确保是第一个。
    Optional<Integer> any = simpleList.parallelStream().findAny();
    System.out.println("first = " + first.get());
    System.out.println("any = " + any.get());
}

@Test
public void matchTest(){
    // 判断有没有任意一个人年龄大于35岁
    boolean flag = personList.stream().anyMatch(item -> item.getAge() > 35);
    System.out.println("flag = " + flag);

    // 判断是不是所有人年龄都大于35岁
    flag = personList.stream().allMatch(item -> item.getAge() > 35);
    System.out.println("flag = " + flag);
}

```

#### (2)统计(count/averaging/sum/max/min)

```java
@Test
    public void countTest(){
        //统计有多少人
        long count = personList.stream().count();
        System.out.println("count = " + count);
        //统计平均薪资——集合编程的流不能直接进行运算，先编程数字类型的流
        OptionalDouble average = simpleList.stream().mapToInt(i -> i).average();
        average.ifPresent(System.out::println);

        //求和
        int sum = IntStream.of(1, 2, 3, 4).sum();
        System.out.println("sum = " + sum);
        //最大值
        //new一个Random，然后使用ints()随机生成一个IntStream，使用max()得到一个Optional，如果存在就输出
        OptionalInt max = new Random().ints(20).max();
        max.ifPresent(value-> System.out.println("value = " + value));
        //最小值
        OptionalInt min = new Random().ints(20).min();
        min.ifPresent(System.out::println);

        //求工资最高的人
                                                        //将Person中的Salary按照返回的int类型比较器进行比较
        Optional<Person> max1 = personList.stream().max(Comparator.comparingInt(Person::getSalary));
        max1.ifPresent(System.out::println);

    }

```

#### (3)归约(reduce)

`把一堆的数据整合成一个`——求和、求乘积

需要两个参数，并且有一个返回值的一种函数式接口，其实也是Functional类型的

```java
@Test
public void reduceTest(){
    //传入的参数，第一个是初始值，如果是加法就是0，乘法就是1，n1是结果，n2是当前遍历值，通过乘法后把结果给n1
    int reduce = IntStream.of(1, 2, 3, 4).reduce(1, (n1, n2) -> n1 * n2);
    int reduce1 = IntStream.of(1, 2, 3, 4).reduce(0, (n1, n2) -> n1 + n2);
    System.out.println("reduce = " + reduce);
    System.out.println("reduce1 = " + reduce1);
}

```

#### (4)接合(joining)

`joining`可以将stream中的元素使用某种连接符连接起来(没有的话，直接连接)，连接成一个字符串

```java
@Test
public void joiningTest(){
    List<String> list = Arrays.asList("a", "b", "c");
    //collect是收集，把流中的元素收集起来
    String collect = list.stream().collect(Collectors.joining("---"));
    System.out.println("collect = " + collect);
}

```

#### (5)分组(partitioningBy分区和groupingBy分组)

- 分区：将`stream`按条件分为两个`Map`，比如员工按薪资是否高于8000分为两部分。
- 分组：将集合分为多个Map，比如员工按性别分组。

```java
@Test
public void groupTest() {
    //根据判断的真假进行分区
    Map<Boolean, List<Person>> collect = personList.stream().collect(Collectors.partitioningBy(p -> p.getSalary() > 5000));
    //根据性别进行分组
    Map<String, List<Person>> collect1 = personList.stream().collect(Collectors.groupingBy(Person::getSex));
    System.out.println("collect = " + collect);
    System.out.println("collect1 = " + collect1);
}

```

#### (6)归集(collect)

```java
@Test
public void collectTest() {
    /**
         * 转Map的时候key和value的时候需要进行处理
         */
    List<Integer> collect = simpleList.stream().collect(Collectors.toList());
    Set<Integer> collect1 = simpleList.stream().collect(Collectors.toSet());
    Map<String, Person> collect2 = personList.stream().collect(Collectors.toMap(person -> person.getName(), person -> person));
    System.out.println(collect2.get("张三"));
}

```

### 3、中间操作

#### (1)筛选(filter)

```java
//筛选出来工资大于5000的人，然后重新归集成出来，然后转成一个List进行输出
@Test
public void filterTest(){
    List<Person> collect = personList.stream().filter(p -> p.getSalary() > 5000).collect(Collectors.toList());
    System.out.println(collect);
}

```

#### (2)映射(map)

```java
@Test
public void mapTest(){
    //需要一个返回值
    Stream<Integer> integerStream = personList.stream().map(Person::getSalary);
    System.out.println(integerStream);
    personList.stream().map(p->{
      p.setSalary(p.getSalary()+1000);
      return p;
    }).forEach(System.out::println);
}

```

#### (3)peek操作

使用peek进行中间的操作，比如上面的添加工资的映射就可以通过peek实现

```java
List<Person> collect = personList.stream().filter(person -> person.getSalary() > 5000)
        .peek(person -> person.setSalary(person.getSalary()+1000))
        .collect(Collectors.toList());

```

### 4、其他操作

流也可以进行合并、去重、限制、跳过等操作。

```java
@Test
public void otherTest(){
    // distinct去掉重复数据   
    // skip跳过几个数据
    // limit限制使用几个数据
    simpleList.stream().distinct().skip(2).limit(3).forEach(System.out::println);
}

//  11,11,22,22,11,23,43,55,78
//  去重  11，22,23,43,55,78
//  掉过两个  23，43,55,78
// 使用3个    23,43,55

```



# 第十五章 IO流(输入输出流)

​	集合中的Stream也是流，但是它是使用函数式编程数据处理，一个数据集通过函数式编程回变成一个新的数据集。

​	而IO流主要用来数据传输的，跨越介质之间传输，就有输入和输出(数据通过介质传输，从a->b、或者从磁盘到内存)，存在输入和输出就有流的传输。

## 一、IO流的基本概念

​	Java的IO是实现输入和输出的基础，可以方便的实现数据的输入和输出操作。在Java中把对于输入/输入操作是以流的方式进行操作的。java.io 包下提供了大量的供我们使用的操作【流】的方法和接口，用于进行各类数据的处理和传输。

​	计算机的输入和输出都是通过二进制来完成的。在网络中我们要传递数据就要将数据【流化】，换句话说就是将文件、复杂的对象转化成能够在网络上传输的一个个的0和1，我在这里先画几幅图帮助大家理解一下。

文件在磁盘的传输：

![image-20210812143541971](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812143541971.png)

文件在网络的传输：

![image-20210812143608400](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812143608400.png)

内存中对象的输入输出：

![image-20210812144810455](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812144810455.png)



## 二、文件的操作

1、文件路径

'\\'在Java中是转义符，把有些有特殊意义的字符转义成某一个其他的表达方式(屏蔽掉符号的特殊意义)。

​	正斜杠，又称左斜杠，符号是"/"；反斜杠，也称右斜杠，符号是"\\" 。

​	在Unix/Linux中，路径的分隔采用正斜杠"/"，比如"/home/hutaow"；而在Windows中，路径分隔采用反斜杠"\"，比如"C:\Windows\System"

在Java当中反斜杠代表的是转义：

比如:

制表符（也叫制表位）的功能是在不使用表格的情况下在垂直方向按列对齐文本，就是咱们的Tab键。

- \\" 将双引号转义为真正的双引号
- ‘\r’ (回车)：即将光标回到当前行的行首(而不会换到下一行)，之后的输出会把之前的输出覆盖
- ‘\n’ 换行，换到当前位置的下一位置，而不会回到行首

### 2、File类简介

​	在 Java 中，File 类是 java.io 包中唯一代表磁盘文件本身的对象。File 类定义了一些与平台无关的方法来操作文件，File类主要用来获取或处理与磁盘文件相关的信息，像文件名、 文件路径、访问权限和修改日期等，还可以浏览子目录层次结构。
​	File 类表示处理文件和文件系统的相关信息。也就是说，File 类不具有从文件读取信息和向文件写入信息的功能，它仅描述文件本身的属性。

### 3、构造方法

| 构造器                           | 描述                                                   |
| -------------------------------- | ------------------------------------------------------ |
| File(String pathname)            | 通过将给定路径名字符串来创建一个新 File 实例           |
| File(String parent,String child) | 根据指定的父路径和文件路径创建一个新File对象实例       |
| File(File parent,String child)   | 根据指定的父路径对象和文件路径创建一个新的File对象实例 |

```java
@Test
    public void testCreateFile() {
        //全路径名创建对象——使用字符串的形式进行创建
        File file = new File("J:\\typora\\图片\\javese元动力文件");
        //父类文件夹和子类文件名创建对象——使用字符串的形式进行创建
        File file1 = new File("J:\\typora\\图片\\javese元动力文件", "javase学习全资料.md");
        //第三种构造方法：获得父亲的文件夹，然后new对象的时候传入——使用文件的形式进行创建
        File file2 = new File("J:\\typora\\图片\\javese元动力文件");
        File file3 = new File(file2, "javase学习全资料.md");
    }
```

### 4、常用方法

```java
@Test
public void testFile() throws IOException {
    File parentFile = new File("J:\\code\\File\\test1.txt");
    //如果这个文件不存在就新建
    if (!parentFile.exists()) {
        boolean newFile = parentFile.createNewFile();
        System.out.println(newFile ? "创建成功" : "创建失败 ");
    }
    //输出父亲的地址
    System.out.println("parentFile.getParent() = " + parentFile.getParent());
    //输出地址
    System.out.println("parentFile.getName() = " + parentFile.getName());
    //是不是一个文件
    System.out.println("parentFile.isFile() = " + parentFile.isFile());
    //是不是一个文件夹
    System.out.println("parentFile.isDirectory() = " + parentFile.isDirectory());
    //是不是可读
    System.out.println("parentFile.canRead() = " + parentFile.canRead());
    //父亲文件夹的名字
    System.out.println("parentFile.getParent() = " + parentFile.getParent());
    //全路径名
    System.out.println("parentFile.getAbsoluteFile() = " + parentFile.getAbsoluteFile());
    //通过此抽象路径名返回分区 named的大小
    System.out.println("parentFile.getTotalSpace() = " + parentFile.getTotalSpace());
    //返回此抽象路径名表示的文件上次修改的时间
    System.out.println("parentFile.lastModified() = " + parentFile.lastModified());
    parentFile.renameTo(new File("J:\\code\\File\\test2.txt"));
}
```

### 5、File类创建和删除功能

|         |                 |                                                              |
| ------- | --------------- | ------------------------------------------------------------ |
| boolean | createNewFile() | 指定路径不存在该文件时创建文件，返回true 否则false           |
| boolean | mkdir()         | 当指定的单击文件夹不存在时创建文件夹并返回true 否则false     |
| boolean | mkdirs()        | 当指定的多级文件夹在某一级文件夹不存在时，创建多级文件夹并返回true 否则false |
| boolean | delete()        | 删除文件或者删除单级文件夹                                   |

### 6、File类的判断功能

|         |               |                                    |
| ------- | ------------- | ---------------------------------- |
| boolean | exists()      | 判断指定路径的文件或文件夹是否为空 |
| boolean | isAbsolute()  | 判断当前路径是否是绝对路径         |
| boolean | isDirectory() | 判断当前的目录是否存在             |
| boolean | isFile()      | 判断当前的目录是否是一个文件       |
| boolean | isHidden()    | 判断当前路径是否是一隐藏文件       |

### 7、File类的获取功能和修改名字功能

|         |                     |                                                      |
| ------- | ------------------- | ---------------------------------------------------- |
| File    | getAbsoluteFile()   | 获取文件的绝对路径，返回File对象                     |
| String  | getAbsolutePath()   | 获取文件的绝对路径，返回路径的字符串                 |
| String  | getParent()         | 获取当前路径的父级路径，以字符串形式返回该父级路径   |
| String  | getName()           | 获取文件或文件夹的名称                               |
| String  | getPath()           | 获取File对象中封装的路径                             |
| long    | lastModified()      | 以毫秒值返回最后修改时间                             |
| long    | length()            | 返回文件的字节数                                     |
| boolean | renameTo(File dest) | 将当前File对象所指向的路径修改为指定File所指向的路径 |

### 8、文件夹列表操作

| 返回值   | 方法                             | 描述                                                 |
| -------- | -------------------------------- | ---------------------------------------------------- |
| String   | list()                           | 得到这个文件夹下的所有文件，返回路径数组             |
| String[] | list(FilenameFilter filter)      | 通过过滤器过滤文件，过滤通过文件名过滤，返回路径数组 |
| File[]   | listFiles()                      | 得到这个文件夹下的所有文件，返回文件数组             |
| File[]   | listFiles(FileFilter filter)     | 通过过滤器过滤文件，过滤通过文件过滤，返回文件数组   |
| File[]   | listFiles(FilenameFilter filter) | 通过过滤器过滤文件，过滤通过文件名过滤，返回文件数组 |

### 9、作业

```java
public class PngFile {

    public static void main(String[] args) {
        PngFile pngFile = new PngFile();
        pngFile.FileAllImg(new File("J:\\typora\\图片\\javese元动力文件"));
    }

    public void FileAllImg(File file) {
        MyFile myFile = new MyFile();
        //获取此路径下的所有文件，list()可以传入参数，是一个函数式接口，使用lambda表达式或者内部类实现
        //这里箭头函数中的f是parent的文件名，所以一定是文件夹，name是子文件夹的名字
        File[] listStringArray = file.listFiles(myFile);
        //直接得到这个文件夹中的所有子文件，但是会出现空指针异常，就添加一个判断
        if (listStringArray == null || listStringArray.length == 0) {
            return;
        }
        //遍历所有文件，看看是不是文件夹，如果是，就进行递归，判断子文件夹，如果是就判断文件名字是不是有png
        for (int i = 0; i < listStringArray.length; i++) {
            boolean directory = listStringArray[i].isDirectory();
            if (directory) {
                //如果是文件夹，就判断子文件还是不是文件夹，使用递归
                FileAllImg(listStringArray[i]);
            } else {
                //如果不是文件夹，就判断是不是png文件，然后输出
                String name = listStringArray[i].getName();
                if (name.contains("png"))
                    System.out.println(name);
            }
        }


    }
    /**
     * Filter用来过滤的
     * 可以很简单，可以很复杂
     */
    class MyFile implements FilenameFilter {

        @Override
        public boolean accept(File pathname, String name) {
            return pathname.isDirectory() || name.contains("png");
        }
    }

}
```

## 三、IO流分类

​	Java中一切皆对象，流也是对象，在学习之前我们不妨先看分类和概念，至于是哪个类其实没那么重要。

​	其实说到流，我们能想到流水，其实这已经很形象了，水从汪洋大海流入湖泊就是要通过河流。如果你还不知道，接着往下看。

​	其实到目前为止，我们对流已经有了基本的概念，接下来我们就要深入学习流了。按照不同的分类方式，可以把流分为不同的类型。常用的分类有三种：

​	`读东西的时候需要向内核申请，先是Java程序向内核申请从磁盘中读内容，然后内核开始读，读到内核空间，Java代码只能等内核去读，读完的时候Java再从内核空间把代码复制到堆中(用户空间)。`

​	`怎么知道读完了：1、派一个小弟线程一直问，2、内核空间主动通知`

### 1、 按照流向分(BIO-阻塞IO)

- 输入流： 只能从中读取数据，而不能向其写入数据。
- 输出流：只能向其写入数据，而不能向其读取数据。

![image-20210812160823989](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812160823989.png)

![image-20210812161248102](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812161248102.png)	当然系统级别的方法调用我们可以暂时不用考虑。但是我们确确实实看到一个文件在传输过程中经历了很多次的拷贝，IO的性能本来就不是很高，所以后来又有了零拷贝、Nio等技术，这些知识点我们计划在附加课讲解。

### 2 、按照操作单元划分

- 字节流：是一个字节一个字节的读取或写入
- 字符流：是一个字符一个字符的读取或写入，一个字符就是两个字节，主要用来处理字符。

### 3、 按照角色划分

- 节点流：直接从/向一个特定的IO设备（如磁盘，网络）读/写数据的流，称为节点流。
- 处理流：“连接”在已存在的流（节点流或处理流）之上通过对数据的处理为程序提供更为强大的读写功能的流。

![image-20210812162235651](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812162235651.png)

`节点流就是new的时候传一个文件` `处理流就是new的时候传一个其他流，对流进行一些更复杂的处理`

`水箱相当于文件，节点流就是传输文件的，处理流就是对文件进行中间操作`

### 4、Java输入/输出流体系中常用的流的分类表

|       分类       |      字节输入流      |      字节输出流       |   字符输入流    |   字符输出流    |
| :--------------: | :------------------: | :-------------------: | :-------------: | :-------------: |
| 抽象基类`(接口)` |     InputStream      |     OutputStream      |     Reader      |     Writer      |
|     访问文件     |   FileInputStream    |   FileOutputStream    |   FileReader    |   FileWriter    |
|     访问数组     | ByteArrayInputStream | ByteArrayOutputStream | CharArrayReader | CharArrayWriter |
|    访问字符串    |                      |                       |  StringReader   |  StringWriter   |
|  缓冲流（处理）  | BufferedInputStream  | BufferedOutputStream  | BufferedReader  | BufferedWriter  |
|     操作对象     |  ObjectInputStream   |  ObjectOutputStream   |                 |                 |

## 四、流的案例

### 1、继承关系

InputStream和OutputStream

![image-20210812164824415](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812164824415.png)

Reader和Writer

![image-20210812164846302](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812164846302.png)

### 2、流怎么用

#### (1)将一个流对象插在一个节点上：

其实通过名字我们就可以很好的理解了：FileInputStream就是怼在文件上的输入流啊！

```java
public abstract class InputStream implements Closeable
```

InputStream本身是抽象类，我们需要使用它的子类去构造对象：

```java
InputStream inputStream = new FileInputStream(file);
```

既然是输入流就要一点一点的往内存里读数据啊！

![image-20210812165322884](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/io%E6%B5%81.assets/image-20210812165322884.png)

其实inputStream的方法并不多，关键在于几个read方法，管子已经插上了，接下来就是读了。

```
// 读一个字节
int read = inputStream.read();

// 一次性读1024个字节到那个内存数组
int read = inputStream.read(new byte[1024]);

// 从第0个字节开始读，读120个字节
int read = inputStream.read(new byte[1024],0,120);
```



#### (2)使用read()获取

```java
@Test
    public void testRead() throws IOException {
        File file = new File("J:\\code\\File\\a.txt");
        //创建一个字节读取流，把这个流插进节点——节点就是一个文件
        InputStream inputStream = new FileInputStream(file);
        int read;
        int i = 0;
        byte[] bytes = new byte[10];
//        while ((read = inputStream.read()) != -1){
//            byte b = (byte)read;
//            bytes[i++] = b;
//        }
        System.out.println(new String(bytes));
        byte[] b2 = new byte[3];
        int len = 0;
        StringBuilder sb = new StringBuilder();
        //read将读到的数据传进byte数组，然后把返回一个int——读取了几个数据
        while ((read = inputStream.read(b2)) != -1){
            //每次读到几个字节，就把读到的字节转成一个字符串，然后放进一个可变字符串序列中，直至读完
            String s = new String(b2, 0, len);
            sb.append(s);
        }
        System.out.println(sb);
    }
```

#### (3)使用write()写

```java
 @Test
    public void testWrite() throws IOException {
        byte[] bytes = {97, 98, 99, 100};
        //把字节数组输出到文件上，如果boolean传入false就是覆盖，true就是追加，详看源码boolean解释
        OutputStream outputStream = new FileOutputStream("J:\\code\\File\\a.txt", true);
        outputStream.write("helloworld".getBytes());
    }
```

#### (4)文件的拷贝

```java
@Test
    public void testCopy() throws IOException {
        //输入流建立在文件上
        FileInputStream fileInputStream = new FileInputStream("J:\\下载\\写真\\入册\\ka6b2340(景颢,张慧萍,入册).jpg");

        //建立一个输出流
        File file = new File("J:\\code\\File\\abc.jpg");
        FileOutputStream outputStream = new FileOutputStream(file);

        //一边读，一边写
        long start = System.currentTimeMillis();
        int read;
        byte[] buf = new byte[1024 * 1024];
        int len;
        while ((len = fileInputStream.read(buf)) != -1){
            outputStream.write(buf);
        }
        long end = System.currentTimeMillis();
        System.out.println(end - start);
    }
```

#### (5)代码简化

流定义在try后面的()中，使用分号隔开

```java
@Test
    public void testCopy() {



        try( FileInputStream fileInputStream = new FileInputStream("J:\\下载\\写真\\入册\\ka6b2340(景颢,张慧萍,入册).jpg");
             FileOutputStream outputStream = new FileOutputStream("J:\\code\\File\\abc.jpg");
        )
        {
//            if (new Random().nextInt(10) > 2){
//                throw new IOException();
//            }
            //输入流建立在文件上

            //建立一个输出流


            //一边读，一边写
            long start = System.currentTimeMillis();
            int read;
            byte[] buf = new byte[1024 * 1024];
            int len;
            while ((len = fileInputStream.read(buf)) != -1) {
                outputStream.write(buf);
            }
            long end = System.currentTimeMillis();
            System.out.println(end - start);
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
```

#### (6)使用char数组

```java
@Test
public void testReaderWriter() throws IOException {
    FileReader fileReader = new FileReader("J:\\code\\File\\abc.txt");
    FileWriter fileWriter = new FileWriter("J:\\code\\File\\bbb.txt");
    char[] chars = new char[1024];
    int len;
    while ((len = fileReader.read(chars)) != -1){
        fileWriter.write(chars, 0, len);
    }
    fileReader.close();
    fileWriter.close();
}
```

#### (7)使用处理流

读整行

```java
@Test
public void testBuffReader() throws IOException {
    Reader reader = new FileReader("J:\\code\\File\\a.txt");

    BufferedReader bufferedReader = new BufferedReader(reader);
    String b;
    while((b = bufferedReader.readLine()) != null){
        System.out.println(b);
    }
    bufferedReader.close();
    reader.close();
}
```

写整行，并且换行

```java
 public static void main(String[] args)throws IOException {
     Writer writer = new FileWriter("J:\\code\\File\\a.txt");
     BufferedWriter bufferedWriter = new BufferedWriter(writer);
     while(true){
         Scanner scanner = new Scanner(System.in);
         String next = scanner.next();
         bufferedWriter.write(next);
         bufferedWriter.newLine();
         bufferedWriter.flush();
     }
```



## 五、序列化和反序列化

### 1、对象序列化

- 序列化：将对象写入到IO流中，说的简单一点就是将内存模型的对象变成字节数字，可以进行存储和传输。
- 反序列化：从IO流中恢复对象，将存储在磁盘或者从网络接收的数据恢复成对象模型。
- 使用场景：所有可在网络上传输的对象都必须是可序列化的，否则会出错；所有需要保存到磁盘的Java对象都必须是可序列化的。
- 被序列化的对象必须实现`Serializable`这个接口，才能被序列化

```java
FileOutputStream outputStream = new FileOutputStream("J:\\code\\File\\a.txt");
//如果只有new ObjectOutputStream是不对的，因为需要把对象传入磁盘，所以需要传一个文件的outputStream
ObjectOutputStream objectOutputStream = new ObjectOutputStream(outputStream);//我们需要另外一个流来包装
```

- 序列化

```java
@Test
public void testObjectWriterStream() throws IOException {
    FileOutputStream outputStream = new FileOutputStream("J:\\code\\File\\a.txt");
    //如果只有new ObjectOutputStream是不对的，因为需要把对象传入磁盘，所以需要传一个文件的outputStream
    ObjectOutputStream objectOutputStream = new ObjectOutputStream(outputStream);
    objectOutputStream.writeObject(new User(12));
    objectOutputStream.close();
    outputStream.clos\e();
}
```

- 反序列化

```java
@Test
public void testObjectReaderStream() throws IOException, ClassNotFoundException {
    InputStream inputStream = new FileInputStream("J:\\code\\File\\a.txt");
    ObjectInputStream objectInputStream = new ObjectInputStream(inputStream);
    User user1 = (User)objectInputStream.readObject();
    System.out.println(user1.getAge());
    inputStream.close();
    objectInputStream.close();
}
```

需要版本序列号的原因

- 编译过程中代码会发生改变
- Jdk版本不同
- 所以需要一个通用的序列化版本号，不同的程序看见这个序列化版本号就直接序列化

### 2、序列化版本号

​		我们知道，**反序列化必须拥有class文件，但随着项目的升级，class文件也会升级，序列化怎么保证升级前后的兼容性呢？**

​		Java序列化提供了一个``private static final long serialVersionUID` 的序列化版本号，只要版本号相同，即使更改了序列化属性，对象也可以正确被反序列化回来。

```java
public class Person implements Serializable {
    //序列化版本号
    private static final long serialVersionUID = 1111013L;
    private String name;
    private int age;
    //省略构造方法及get,set
}
```

序列化版本号可自由指定，如果不指定，JVM会根据类信息自己计算一个版本号，这样随着class的升级、代码的修改等因素无法正确反序列化；

​		不指定版本号另一个明显隐患是，不利于jvm间的移植，可能class文件没有更改，但不同jvm可能计算的规则不一样，这样也会导致无法反序列化。

什么情况下需要修改serialVersionUID呢：

- 如果只是修改了方法，反序列化不容影响，则无需修改版本号；
- 如果只是修改了静态变量，瞬态变量（transient修饰的变量），反序列化不受影响，无需修改版本号。

### 3、总结

1. 所有需要网络传输的对象都需要实现序列化接口。
2. 对象的类名、实例变量（包括基本类型，数组，对其他对象的引用）都会被序列化；方法、类变量、transient实例变量都不会被序列化。
3. 如果想让某个变量不被序列化，使用transient修饰。
4. 序列化对象的引用类型成员变量，也必须是可序列化的，否则，会报错。
5. 反序列化时必须有序列化对象的class文件。
6. 同一对象序列化多次，只有第一次序列化为二进制流，以后都只是保存序列化编号，不会重复序列化。
7. 建议所有可序列化的类加上serialVersionUID 版本号，方便项目升级。

### 4、拷贝

什么叫拷贝？

​	`b = a;`是改变引用的不是拷贝，拷贝是在内存中重新开辟一片空间，然后将b指向新的空间；浅拷贝只拷贝User，不拷贝User下的Dog，拷贝出来的User仍然指向的是原来的Dog；而深拷贝是既拷贝User，也拷贝Dog

![1660291703611](%E5%9B%BE%E7%89%87/1660291703611.png)

- 浅拷贝

```java
@Test
    public void testDeepCopy() throws CloneNotSupportedException {
        User user = new User(22,"张三");
        user.setDog(new Dog(2));

        //返回值是Object，必须强转,User还要实现Cloneable接口
        User user1 = (User) user.clone();
        user1.getDog().setAge(100);
        System.out.println(user);
    }
```

- 深拷贝

```java
public class DeepCopyUtil {
    public static <T> T deepCopy(T t) throws IOException, ClassNotFoundException {
        //定义对象

        //将对象写进字节数组中
        //其中有一个方法，最后会返回一个byte数组，读完了，再去调用toByteArray的时候，能把读到的信息返回一个Byte数组
        ByteArrayOutputStream outputStream = new ByteArrayOutputStream();//字节数组输出流
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(outputStream);//对象输出流，参数是输出位置
        objectOutputStream.writeObject(t);//输出对象

        //获取字节数组
        //刚开始没有toByteArray这个方法，但是需要将静态类型和实际类型相同，就可以使用子类特有的方法
        //byte数组必须在读完的时候才使用
        byte[] bytes = outputStream.toByteArray();

        //用输入流读出来,已经写进去了，现在读出来，从那个Byte数组中读出来
        ByteArrayInputStream byteArrayInputStream = new ByteArrayInputStream(bytes);
        ObjectInputStream objectInputStream = new ObjectInputStream(byteArrayInputStream);
        Object object = objectInputStream.readObject();

        //关闭流——后打开的先关
        objectInputStream.close();
        byteArrayInputStream.close();
        objectOutputStream.close();
        outputStream.close();
        return (T)object;
    }
}
```



# 第十六章 注解和反射

## 一、注解

Java 注解（Annotation）又称 Java 标注，是 JDK5.0 引入的一种机制。Java 语言中的类、方法、变量、参数和包等都可以被标注。

注解是来告诉编译器的，告诉idea、jdk看见注解需要怎么操作。

SURCE——编译器，javac

CLASS——jvm

RUNTIME——自己写的程序也能看见，保存到内存中

### 1、Annotation 的定义

```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.SOURCE)
public @interface Override {
}

@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
public @interface FunctionalInterface {}
```

我们仿照jdk自带注解的方式，自己定义一个注解：

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface MyAnnotation {
}
```

结果发现这个注解确实可以使用了，同时我们看到了这几个注解`@Retention` 和 `@Target` 这两个注解专门给注解加注解，我们称之为元注解。

![image-20210912144431542](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912144431542.png)

再来分析，我们不妨看看那几个元注解的源码：

```java
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.ANNOTATION_TYPE)
public @interface Retention {
    /**
     * Returns the retention policy.
     * @return the retention policy
     */
    RetentionPolicy value();
}
```

我们发现注解中可以有方法，我们在注解中可以这样定义方法：

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface MyAnnotation {
    String name() default "jerry";
    int age();
}
```

我们在使用的时候就可以这样使用了：

![image-20210912144933048](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912144933048.png)

关于注解方法，有以下几点注意的：

1、定义的格式是：String name();

2、可以有默认值，也可以没有，如果没有默认值在使用的时候必须填写对应的值。默认值使用default添加。

3、如果想在使用的时候不指定具体的名字，方法名字定义为value() 即可。

```
public @interface MyAnnotation {
    String name() default "jerry";
    int value();
}
```

![image-20210912145304383](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912145304383.png)

​		看到这里，有人可能会问，注解到底有什么用？如果我们没有学习反射，对我们而言，注解确实没什么用，哈哈哈，后边我们结合反射会有例子讲解。



### 2、Annotation 组成部分

我们使用javap查看生成的注解类：

```java
PS D:\code\test\out\production\test\com\ydlclass\chat> javap -v .\MyAnnotation.class
Classfile /D:/code/test/out/production/test/com/ydlclass/chat/MyAnnotation.class
  Last modified 2021-9-12; size 482 bytes
  MD5 checksum 5b096a2faeef11535277c9cdbe5703d0
  Compiled from "MyAnnotation.java"
  //我们发现字节码中注解其实也是一个接口统一继承自java.lang.annotation.Annotation
public interface com.ydlclass.chat.MyAnnotation extends java.lang.annotation.Annotation
  minor version: 0
  major version: 52
  flags: ACC_PUBLIC, ACC_INTERFACE, ACC_ABSTRACT, ACC_ANNOTATION
Constant pool:
{
    // 生成了两个抽象方法
  public abstract java.lang.String name();
    descriptor: ()Ljava/lang/String;
    flags: ACC_PUBLIC, ACC_ABSTRACT
    AnnotationDefault:
      default_value: s#7
  public abstract int value();
    descriptor: ()I
    flags: ACC_PUBLIC, ACC_ABSTRACT
}
SourceFile: "MyAnnotation.java"
RuntimeVisibleAnnotations:
  0: #13(#8=[e#14.#15])
  1: #16(#8=e#17.#18)
PS D:\code\test\out\production\test\com\ydlclass\chat>

```



java Annotation 的组成中，有 3 个非常重要的主干类。它们分别是：

#### （1）Annotation.java

```java
package java.lang.annotation;
public interface Annotation {

    boolean equals(Object obj);

    int hashCode();

    String toString();

    Class<? extends Annotation> annotationType();
}
```



#### （2）ElementType.java

ElementType 是 Enum 枚举类型，它用来指定 Annotation 的类型。大白话就是，说明了我的注解将来要放在哪里。

```java
package java.lang.annotation;

public enum ElementType {
    // 类、接口（包括注释类型）或枚举声明
    TYPE,          
    //  字段声明（包括枚举常量
    FIELD,       
    //  方法声明
    METHOD,       
    //  参数声明
    PARAMETER,      
    //  构造方法声明
    CONSTRUCTOR,     
    //  局部变量声明
    LOCAL_VARIABLE,  
    //   注释类型声明
    ANNOTATION_TYPE,   
    //  包声明
    PACKAGE      
}
```



#### （3）RetentionPolicy.java

​		 RetentionPolicy 是 Enum 枚举类型，它用来指定 Annotation 的策略。通俗点说，就是不同 RetentionPolicy 类型的 Annotation 的作用域不同。

1. 若 Annotation 的类型为 SOURCE，则意味着：Annotation 仅存在于编译器处理期间，编译器处理完之后，该 Annotation 就没用了。 例如，" @Override" 标志就是一个 Annotation。当它修饰一个方法的时候，就意味着该方法覆盖父类的方法；并且在编译期间会进行语法检查！编译器处理完后，"@Override" 就没有任何作用了。
2. 若 Annotation 的类型为 CLASS，则意味着：编译器将 Annotation 存储于类对应的 .class 文件中，它是 Annotation 的默认行为。
3. 若 Annotation 的类型为 RUNTIME，则意味着：编译器将 Annotation 存储于 class 文件中，并且可由JVM读入。

```java
package java.lang.annotation;
public enum RetentionPolicy {
    //Annotation信息仅存在于编译器处理期间，编译器处理完之后就没有该Annotation信息了
    SOURCE,       
    //编译器将Annotation存储于类对应的.class文件中。但不会加载到JVM中。默认行为 
    CLASS,       
    // 编译器将Annotation存储于class文件中，并且可由JVM读入，因此运行时我们可以获取。
    RUNTIME       
}
```



------

### 3、Java 自带的 Annotation

理解了上面的 3 个类的作用之后，我们接下来可以讲解 Annotation 实现类的语法定义了。

#### （1）内置的注解

Java 定义了一套注解，共有10 个，6个在 java.lang`普通注解` 中，剩下 4 个在 java.lang.annotation `元注解`中。

（1）作用在代码的注解是

- @Override - 检查该方法是否是重写方法。如果发现其父类，或者是引用的接口中并没有该方法时，会报编译错误。
- @Deprecated - 标记过时方法。如果使用该方法，会报编译警告。
- @SuppressWarnings - 指示编译器去忽略注解中声明的警告。
- @SafeVarargs - Java 7 开始支持，忽略任何使用参数为泛型变量的方法或构造函数调用产生的警告。
- @FunctionalInterface - Java 8 开始支持，标识一个匿名函数或函数式接口。
- @Repeatable - Java 8 开始支持，标识某注解可以在同一个声明上使用多次。

（2）作用在其他注解的注解(或者说 元注解)是:

- @Retention - 标识这个注解怎么保存，是只在代码中，还是编入class文件中，或者是在运行时可以通过反射访问。
- @Documented - 标记这些注解是否包含在用户文档中。
- @Target - 标记这个注解可以修饰哪些 Java 成员。
- @Inherited - 如果一个类用上了@Inherited修饰的注解，那么其子类也会继承这个注解



#### （2）常用注解

​		通过上面的示例，我们能理解：@interface 用来声明 Annotation，@Documented 用来表示该 Annotation 是否会出现在 javadoc 中， @Target 用来指定 Annotation 的类型，@Retention 用来指定 Annotation 的策略。

> @Documented  标记这些注解是否包含在用户文档中。

> @Inherited

@Inherited 的定义如下：加有该注解的注解会被子类继承，注意，仅针对**类，成员属性**、方法并不受此注释的影响。

```java
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.ANNOTATION_TYPE)
public @interface Inherited {
}
```





> @Deprecated

@Deprecated 的定义如下：

```java
@Documented
@Retention(RetentionPolicy.RUNTIME)
public @interface Deprecated {
}
```

说明：

 @Deprecated 所标注内容，不再被建议使用。

![image-20210912151947844](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912151947844.png)

加上这个注解在使用或者重写时会有警告：

![image-20210912152418045](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912152418045.png)





> @SuppressWarnings

@SuppressWarnings 的定义如下：

```
@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
@Retention(RetentionPolicy.SOURCE)
public @interface SuppressWarnings {
    String[] value();
}
```

说明：

​		SuppressWarnings 的作用是，让编译器对"它所标注的内容"的某些警告保持静默，用于抑制编译器产生警告信息。。例如，"@SuppressWarnings(value={"deprecation", "unchecked"})" 表示对"它所标注的内容"中的 "SuppressWarnings 不再建议使用警告"和"未检查的转换时的警告"保持沉默。

![image-20210912152848064](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912152848064.png)



![image-20210912152804165](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210912152804165.png)



不用记，谁记谁傻X。

| **关键字**  | **用途**                                           |
| ----------- | -------------------------------------------------- |
| all         | 抑制所有警告                                       |
| boxing      | 抑制装箱、拆箱操作时候的警告                       |
| fallthrough | 抑制在switch中缺失breaks的警告                     |
| finally     | 抑制finally模块没有返回的警告                      |
| rawtypes    | 使用generics时忽略没有指定相应的类型               |
| serial      | 忽略在serializable类中没有声明serialVersionUID变量 |
| unchecked   | 抑制没有进行类型检查操作的警告                     |
| unused      | 抑制没被使用过的代码的警告                         |





### 4、Annotation 的作用

（1）Annotation 具有"让编译器进行编译检查的作用“，这个讲了很多了。

（2）利用反射，和反射配合使用能产生奇妙的化学反应。





## 二、反射

`类在加载的过程中会给每一个类生成一个class文件，我们可以通过class文件访问在方法区中的类`

> 使用反射可以直接操作类对象，操作权限非常高

我们都知道光是可以反射的，我们无法直接接触方法区中一个类的方法、属性、注解等，那就可以通过一面镜子观察它的全貌，这个镜子就是JDK给我们提供的Class类。

![image-20210913095552369](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E5%8F%8D%E5%B0%84.assets/image-20210913095552369.png)

首先我们看一下Class这个类，初步简单的分析一下。我们发现这个类并没有什么成员变量，仅仅存在许多的方法，还有不少是本地方法。通过这些方法的名字我们大致能猜出，这个类能帮我们获取方法、构造器、属性、注解等。

```java
public final class Class<T>  {

    // 获得他实现的接口
    public Class<?>[] getInterfaces() {
        ReflectionData<T> rd = reflectionData();
        if (rd == null) {
            // no cloning required
            return getInterfaces0();
        } else {
            Class<?>[] interfaces = rd.interfaces;
            if (interfaces == null) {
                interfaces = getInterfaces0();
                rd.interfaces = interfaces;
            }
            // defensively copy before handing over to user code
            return interfaces.clone();
        }
    }

    private native Class<?>[] getInterfaces0();   

    // 获得方法
    @CallerSensitive
    public Method[] getMethods() throws SecurityException {
        checkMemberAccess(Member.PUBLIC, Reflection.getCallerClass(), true);
        return copyMethods(privateGetPublicMethods());
    }

    // 获得他的构造器
    @CallerSensitive
    public Constructor<?>[] getConstructors() throws SecurityException {
        checkMemberAccess(Member.PUBLIC, Reflection.getCallerClass(), true);
        return copyConstructors(privateGetDeclaredConstructors(true));
    }

    // 获得他的属性
    @CallerSensitive
    public Field getField(String name)
        throws NoSuchFieldException, SecurityException {
        checkMemberAccess(Member.PUBLIC, Reflection.getCallerClass(), true);
        Field field = getField0(name);
        if (field == null) {
            throw new NoSuchFieldException(name);
        }
        return field;
    }

}
```

​		我们已经学过了类的加载过程，这里我们要介绍的是，每一个类加载完成后会在方法区生成一个Class类型的对象，辅助我们访问这个的方法、构造器、字段等。这个对象是Class的子类，每个类【有且仅有】一个Class类，也叫类对象。

### 1、获取类对象的方法

#### （1）获取方式

```java
1、使用类
Class clazz = Dog.class;

2、使用全类名
Class aClass = Class.forName("com.ydl.Dog");

3、使用对象
//使用对象
Dog dog = new Dog();
//继承自Dog泛型通配符
Class<? extends Dog> aClass = dog.getClass();
```

#### （2）对类对象操作

```java
//获取类名字
String name = clazz.getName();
//获取类加载器
ClassLoader classLoader = clazz.getClassLoader();
//获取资源
URL resource = clazz.getResource("");
//得到父类
Class superclass = clazz.getSuperclass();
//判断一个类是不是接口，数组等等
boolean array = clazz.isArray();
boolean anInterface = clazz.isInterface();

//重点，使用class对象实例化一个对象
Object instance = clazz.newInstance();
```

### 2、对成员变量的操作

```java
@Test
public void testClassField() throws InstantiationException, NoSuchFieldException, IllegalAccessException {
    //只能拿到public修饰的成员变量的名字
    Field[] fields = dogClass.getFields();
    for (Field field : fields) {
        System.out.println(field.getName());
    }
    System.out.println("----------");
    //获得所有成员属性的名字，包括私有的
    Field[] declaredFields = dogClass.getDeclaredFields();
    for (Field declaredField : declaredFields) {
        System.out.println(declaredField.getName());
    }
    //成员变量的本质就是取值和赋值
    Dog dog = new Dog();
    //获得名字为name的成员变量
    Field name = dogClass.getDeclaredField("name");
    //直接赋值是不可以的，需要获得权限，设置权限为true
    name.setAccessible(true);
    name.set(dog, "toms");
    //返回值是一个Object，知道name是String类型的，进行强转
    String nameStr = (String)name.get(dog);
    System.out.println(nameStr);
}
```

### 3、对成员方法进行操作

```java
//对类对象的方法进行操作
@Test
public void testMethod() throws NoSuchMethodException, InstantiationException, IllegalAccessException, InvocationTargetException {
    //拿到所有的共有的方法，包括父类的
    Method[] methods = dogClass.getMethods();
    for (Method method : methods) {
        System.out.println(method.getName());
    }
    System.out.println("------------");

    //拿到所有在本类中定义的方法，共有的和私有的都拿到
    Method[] declaredMethods = dogClass.getDeclaredMethods();
    for (Method declaredMethod : declaredMethods) {
        System.out.println(declaredMethod.getName());
    }

    //拿到一个方法
    Method eat = dogClass.getDeclaredMethod("eat");
    //传入的是方法名和形参列表，形参列表是类对象
    Method eat1 = dogClass.getDeclaredMethod("eat", String.class);

    //对方法只有一个核心操作，就是调用
    //形参列表是调用哪个对象的方法，后面是调用方法传入的参数
    Dog dog = new Dog();
    //设置权限
    eat.setAccessible(true);
    eat.invoke(dog);
    eat1.invoke(dog, "骨头");
}
```

### 4、对构造器进行操作

```java
//操作构造器
@Test
public void testConstructor() throws NoSuchMethodException, InvocationTargetException, InstantiationException, IllegalAccessException {
    //拿到构造器
    Constructor<Dog> declaredConstructor = dogClass.getDeclaredConstructor();
    //拿到无参构造并且构造一个对象
    Constructor<Dog> declaredConstructor1 = dogClass.getDeclaredConstructor();
    Dog dog = declaredConstructor1.newInstance();//new Dog(); dogClass.Instance()

    //拿到可变参的构造器,传入的是类对象
    Constructor<Dog> declaredConstructor2 = dogClass.getDeclaredConstructor(String.class);
    Dog tom = declaredConstructor2.newInstance("tom");
    System.out.println(tom.getName());

}
```

### 5、对注解进行操作

```java
//操作注解
public void testAnnotation() throws NoSuchFieldException, NoSuchMethodException {
    //通过类对象拿到注解
    Annotation[] annotations = dogClass.getAnnotations();
    MyAnnotation annotation = dogClass.getAnnotation(MyAnnotation.class);

    //通过成员属性拿到注解
    Field name = dogClass.getDeclaredField("name");
    Annotation[] annotations1 = name.getAnnotations();

    Method eat = dogClass.getDeclaredMethod("eat");
    eat.setAccessible(true);
    Annotation annotationEatMethod = eat.getAnnotation(MyAnnotation.class);
}
```

## 三、单例List案例

### 1、拿到所有的class文件

```java
package com.ydlclass.homework.util;

import java.io.File;
import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;

public class FileUtils {

    //遍历文件，根据根目录
    public static void AllFile(String path, List<String> classPaths) {
        //根据路径创建文件进行操作
        File file = new File(path);
        //得到所有符合要求的文件——文件夹和.class文件
        File[] files = file.listFiles((f, n) -> new File(f, n).isDirectory() || n.contains(".class"));
        //如果没有获得的文件或者文件夹直接返回
        if (files == null || files.length == 0) {
            return;
        }
        //对获得的所有文件进行遍历
        for (int i = 0; i < files.length; i++) {
            //判断是不是文件夹
            boolean directory = files[i].isDirectory();
            //如果是文件夹就进行遍历
            if (directory) {
                //因为形参是String，所以传入绝对路径
                AllFile(files[i].getAbsolutePath(), classPaths);
            } else {
                String name = files[i].getName();
                if (name.contains(".class"))
                    classPaths.add(files[i].getAbsolutePath());
            }
        }
    }

    public static List<String> getClassName(File file) {
        List<String> classPaths = new ArrayList<>();
        AllFile(file.getPath(), classPaths);
        //J:\code\test1\out\production\annotationAndReflect\com\ydlclass\Bootstrap.class
        //com.ydlclass.Bootstrap    Class.forName()
        return classPaths.stream().map(path -> {
            //获得绝对路径
            String fileName = file.getAbsolutePath();
            //J:\code\test1\out\production\annotationAndReflect\com\ydlclass\Bootstrap.class
            //com\ydlclass\Bootstrap.class
            //replace是替换，把目标字符串替换成什么字符串
            return path.replace(fileName + "\\", "")
                    .replaceAll("\\\\", ".").replace(".class", "");
        }).collect(Collectors.toList());//搜集转换成一个List

    }

}
```

### 2、维护一个单例集合

```java
package com.ydlclass.homework.context;


import com.ydlclass.Dog;

import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

public class ApplicationContext {
    //维护一个单例环境，一个单例数组
    private static final Map<Class<?>, Object> CONTEXT = new ConcurrentHashMap<>(8);

    //添加单例
    public static void addSingleton(Class<?> clazz, Object entity){
        ApplicationContext.CONTEXT.put(clazz, entity);
    }

    //拿到一个单例对象，传进一个class，然后得到单例对象
    //传入的泛型是知道的，所以可以使用泛型方法
    //这样做的好处是在调用这个方法的时候可以直接返回T类型，不用在调用的时候进行强转
    public static <T> T getSingleton(Class<T> clazz){
        return (T)ApplicationContext.CONTEXT.get(clazz);
    }

    public static void main(String[] args) {
        ApplicationContext.addSingleton(Dog.class, new Dog());
        Dog singleton = ApplicationContext.getSingleton(Dog.class);
    }
}
```

### 3、对拿到的所有class文件进行操作

```java
package com.ydlclass.homework.handler;

import com.ydlclass.homework.annotation.Singleton;
import com.ydlclass.homework.context.ApplicationContext;

import java.util.List;

public class SingletonHandler {
    //创建所有单例
    public static void NewSingleton(List<String> classNames) throws InstantiationException, IllegalAccessException, ClassNotFoundException {
        for (String className : classNames) {
            //根据全限定名称创建class对象
            Class<?> aClass = Class.forName(className);
            //获取注解，如果有这个注解就创建实例对象放进ApplicationContext中的CONTEXT
            if (aClass.getAnnotation(Singleton.class) != null) {
                //根据得到的class创建对象
                Object o = aClass.newInstance();
                //使用静态方法进行添加
                ApplicationContext.addSingleton(aClass, o);
            }

        }
    }
}
```

### 4、这样做的好处

有的类是无状态(成员属性)的，就需要使用这种方法



# 第十七章 网络编程

## 一、网络基本概念

### 1、网卡

​	每一个网卡都有一个被称为MAC地址的独一无二的48位串行号，它被写在卡上的一块内存中。在网络上的每一个计算机都必须拥有一个独一无二的MAC地址。

​	没有任何两块被生产出来的网卡拥有同样的地址。这是因为电气电子工程师协会负责为网络接口控制器（网卡）销售商分配唯一的MAC地址。

### 2、MAC地址、IP地址

window电脑在命令行模式下输入命令：

怎么进入命令行模式，按    win+R，输入cmd即可

![image-20210813150521017](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150521017.png)





```shell
ipconfig -all
```

会看到：

```shell
无线局域网适配器 WLAN:

   描述. . . . . . . . . . . . . . . : Intel(R) Wi-Fi 6 AX201 160MHz
   物理地址. . . . . . . . . . . . . : 8C-C6-81-54-FF-9C
   IPv4 地址 . . . . . . . . . . . . : 192.168.0.109(首选)
   子网掩码  . . . . . . . . . . . . : 255.255.255.0
```

​		其中物理地址指的就是MAC地址、IPv4 地址就是IP。

​		MAC地址也叫物理地址和局域网地址，主要用于确认网上设备的地址，类似于`身份证号`，具有唯一标识，每一个网卡制作完成之后就带有一个MAC地址，永远都不会改变。

​		IP地址，类似于你的现住址，是标记你在网络中的具体位置，一个网卡的IP地址是可以改变的。



IP地址的表示方式：32位

原始

```
01111111.00000000.00000000.00000001
```

十进制表示

```
127.0.0.1
```

### 3、计算机之间发送数据的发展

#### 1） 双绞线

如果只是两台计算机，我们就可以使用双绞线（网线）连载一起，就能互相发送消息，组成一个小网络。

![image-20210813150542149](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150542149.png)





#### （2） 交换机  

​		但是我们的网络不是由两台电脑组成的，我们经常需要将几十台上百台电脑组织起来形成一个局域网，此时一个新的设备就出现了叫做交换机（switch）。

​		交换机可以记录每一个设备的地址和接口的对应关系，从而实现端对端的信息传输。

​		思考问题，交换机要将内容发送给指定的计算机，那么内部一定维护了一张表，记录了哪个电脑链接了我的哪个口。交换机只能识别MAC地址。MAC地址是【物理地址】，交换机对【IP地址】并不感兴趣。



![image-20210813150631723](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150631723.png)





思考一个问题：

交换机是怎么知道这个表的：

![image-20210813150706819](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150706819.png)

交换机效率比较高，而且可以进行桥接。

![image-20210813150719333](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150719333.png)





#### （3）路由器

​		思考：使用交换机可以建立一个超大型的网络吗？

​		一般的交换机的地址表也就能存个几千个地址，当网络内的设备多起来以后，只要交换机找不到对应设备就会广播，地址表如果满了，新地址还会覆盖旧地址就会导致重新寻找效率比较低。所以又引入了一个设备叫【路由器】，谁也听过的一个设备，一般家里都有。

​		注意：路由器不是猫，猫是调制解调器。它能把计算机的【数字信号】翻译成可沿【普通电话线/光纤】传送的模拟信号，而这些模拟信号又可被线路另一端的另一个调制解调器接收，并译成计算机可懂的【语言】。但是运营商送你的盒子一般既有调制解调器的功能，也有路由器的功能，只不过路由功能不太好。

基于路由器，我们提出了以下的设计：

![image-20210813150741372](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150741372.png)





​		这里就有了网络的概念了。以上的几种，哪怕是交换机的桥接也没有涉及IP地址这个概念，都是基于MAC地址进行数据传输。这里有了网络这个抽象概念之后IP地址就应运而生了，IP地址只是用来表示计算机的网络位置，它处于哪一个网络。IP地址和子网掩码共同帮助我们定位一个计算机在网络中的位置。

​		IP地址和子网掩码其实是个32位的二进制数字：



![image-20210813150801640](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150801640.png)



此时发送信息就会再包一个消息的头部

![image-20210813150819122](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150819122.png)

​		家用的路由器，有一个WAN口，有好几个LAN口，wan口用来连接互联网端，LAN用来连接家庭设备。信息在网络传播，依然需要依靠MAC地址，这里有一个ARP协议，就是用来通过IP查找MAC地址的。



![image-20210813150835776](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150835776.png)





来一个栗子，192.168.100.100  发送信息到 192.168.200.101

![image-20210813150854976](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813150854976.png)





> 这种因特网IP地址中特定的专用地址是不作分配的：

①主机号全为“0”。不论哪一类网络，主机号全为“0”表示指向本网，常用在路由表中；

②主机号全为“1”。主机号全为“1”表示广播地址，向特定的所在网上的所有主机发送数据包。



​		IP地址分为五类，A类保留给政府机构，B类分配给中等规模的公司，C类分配给任何需要的人，D类用于组播，E类用于实验，各类可容纳的地址数目不同。

​		A、B、C三类IP地址的特征：当将IP地址写成二进制形式时，A类地址的第一位总是O，B类地址的前两位总是10，C类地址的前三位总是110。

> A类地址

1. A类地址第1字节为网络地址，其它3个字节为主机地址。

2. A类地址范围：1.0.0.1—126.255.255.254

3. A类地址中的私有地址和保留地址，10.X.X.X是私有地址（所谓的私有地址就是在互联网上不使用，而被用在局域网络中的地址）。范围（10.0.0.0-10.255.255.255），127.X.X.X是保留地址，用做循环测试用的。

   

> B类地址

1. B类地址第1字节和第2字节为网络地址，其它2个字节为主机地址。
2. B类地址范围：128.0.0.1—191.255.255.254。
3. B类地址的私有地址和保留地址，172.16.0.0—172.31.255.255是私有地址。

​      

> C类地址

1. C类地址第1字节、第2字节和第3个字节为网络地址，第4个字节为主机地址。另外第1个字节的前三位固定为110。
2. C类地址范围：192.0.0.1—223.255.255.254。
3. C类地址中的私有地址，192.168.X.X是私有地址。(192.168.0.0-192.168.255.255)



> D类地址

1. D类地址不分网络地址和主机地址，它的第1个字节的前四位固定为1110。
2. D类地址范围：224.0.0.1—239.255.255.254
        

> E类地址

1. E类地址不分网络地址和主机地址，它的第1个字节的前五位固定为11110。
2. E类地址范围：240.0.0.1—255.255.255.254

### 4、域名

#### （1）DNS服务器

| 名称       | 介绍                                           | DNS地址                                         |
| ---------- | ---------------------------------------------- | ----------------------------------------------- |
| 114DNS     | 国内用户量最大的老牌DNS                        | 首选：114.114.114.114<br/>备选：114.114.114.115 |
| DNSPod DNS | 中国最大的第三方域名服务商，全球排名第四位     | 首选：119.29.29.29<br/>备选：182.254.116.116    |
| 阿里 DNS   | 阿里公共DNS是阿里巴巴集团推出的DNS递归解析系统 | 首选：223.5.5.5<br/>备选：223.6.6.6             |

#### （2）域名的分类

| 分类标准 | 分类详情                                                     |
| -------- | ------------------------------------------------------------ |
| 语种分类 | 中文：百度.com 、百度.中国、baidu.中国<br>英文：baidu.com    |
| 地区分类 | 中国大陆顶级域名是.cn<br>美国国家顶级域名是.us<br>日本国家顶级域名是.jp |
| 机构分类 | .com  商业性的机构或公司 <br>.org   非盈利的组织、团体      https://apache.org/ <br>.gov   政府部门       http://www.gov.cn/       https://www.shanghai.gov.cn/ |
| 层级分类 | 顶级域名（一级域名)：baidu.com   <br>二级域名：jingyan.baidu.com   www.baidu.com |

## 二、数据的传输

### 1、网络七层参考模型

我们接下来看看ISO参考模型和TCP/IP协议栈的对应关系。

![image-20210813151107369](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813151107369.png)

- TCP/IP是一种结构，标明了每一层是干什么的，哪个协议在哪层，协议是具体的实现

### 2、TCP协议

TCP(Transmission Control Protocol 传输控制协议)是一种面向连接(连接导向)`(需要建立连接)`的、可靠的`(数据不会丢失  )`、 基于IP的传输层协议。提供了流量控制、拥塞控制、超时重传等机制。

TCP是面向链接的，建立链接需要三次握手，三次握手是为了保障双方都知道对方有发送和接收报文的能力。

- 一个计算机有65536个端口
- 一个程序可以启动很多端口，但是一个端口只能被一个程序启动
- TCP协议处理完然后IP协议会做路径选择

![image-20210813164457689](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813164457689.png)

> 三次握手能够保证双方能够互相的接收和发送消息

- seq是随机生成的序列号
- ack是确认序列号
- SYN是建立连接
- ACK是应答位
- 第一次握手：客户端知道能发送信息给服务区，但是不知道服务器能不能接收到
- 第二次握手：客户端知道服务器能接收到消息，服务器知道能发消息给客户端，但是服务器不知道客户端能不能接收到
- 第三次握手：客户端和服务器都知道能给对方发消息，并且知道对方能收到

![image-20210813151258311](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813151258311.png)

> 四次挥手——保证关闭

- 第一次：FIN就是告诉服务器准备关闭，服务器就成为等待关闭状态
- 第二次：服务器回应客户端——确认应答
- 服务端完成关闭连接之前的操作
- 第三次：服务器告诉客户端说断开连接吧
- 第四次：确认应答——关闭连接



![image-20210813151313108](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210813151313108.png)



### 3、UDP协议

​	`不管对方是不是存在，是不是能接收，不管数据会不会丢失，夸夸就是传`

​	UDP(User Datagram Protocol，用户数据报协议)是一种**传输层**的协议，它提供**不可靠**服务，它是无连接的，所以**不存在建立连接需要的时延**。

​	有些场景如直播、电话会议，**能容一些数据的丢失，但是不能允许有较大的时延**。

​	TCP需要在端系统中**维护连接**状态，需要一定的开销。此连接装入包括接收和发送缓存，拥塞控制参数和序号与确认号的参数。UCP不维护连接状态，也不跟踪这些参数，开销小。空间和时间上都具有优势。UDP**提供尽最大努力的交付**，不保证可靠交付。

​	UDP常用一次性传输比较少量数据的网络应用，如DNS,SNMP等，因为对于这些应用，若是采用TCP，为连接的创建，维护和拆除带来不小的开销。UDP也常用于多媒体应用（如IP电话，实时视频会议，流媒体等）数据的可靠传输对他们而言并不重要，TCP的拥塞控制会使他们有较大的延迟，也是不可容忍的

​	![image-20210914100950338](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/%E7%AC%AC12%E7%AB%A0%20%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B.assets/image-20210914100950338.png)

### 4、TCP和UDP的白话对比

- 网卡了，TCP就像看电视一样，卡完之后就继续刚才卡住的地方继续开始了，但是UDP跟看直播一样，卡住的那一段时间就看不上了，不卡了会直接跳到直播开始。
- 对文件安全有要求，使用TCP
- 对速度有要求，使用UDP

## 三、Socket 编程

可以通过调用Socket中的方法，对TCP和UDP进行操作；

用户线程只需要操作Socket中的方法，就可以实现网络互连；

Java中的Socket是将原来的Socket重新抽象了一次；

Socket就是IP+端口号，就是一个插口；

使用Socket相当于连接了两个插口；

![1660478026123](%E5%9B%BE%E7%89%87/1660478026123.png)

### 1、InetAddress

就是把IP地址(还有域名和主机名)封装了，域名找的是互联网中的主机，主机名找的是局域网的主机

#### (1)主机名——找到自己

- 主机名是可以重复的
- 主机名最重要的是找到自己

#### (2)环回地址——指在本身

- 说到环回地址基本都是127.0.0.1，但是127开头的都是环回地址

​	主机用于发送通信的一个特殊地址，访问本机的环回地址可以绕开TCP/IP协议栈的下层。（也就是说：不用再通过什么链路层、物理层、以太网传出去了，而是可以直接在自己的网络层、运输层进行处理了）

​	IPv4的环回地址为：127.0.0.0到127.255.255.255都是环回地址（只是有两个特殊的保留），此地址中的任何地址都不会出现在网络中，网络号为127的地址根本就不是一个网络地址（因为产生的IP数据报就不会到达外部网络接口中，是不离开主机的包）

​	当操作系统初始化本机的TCP/IP协议栈时，设置协议栈本身的IP地址为127.0.0.1（保留地址）。当IP层接收到目的地址为127.0.0.1（准确的说是：网络号为127的IP）的数据包时，不调用网卡驱动进行二次封装，而是立即转发到本机IP层进行处理，由于不涉及底层操作。因此，ping 127.0.0.1一般作为测试本机TCP/IP协议栈正常与否的判断之一。

​	所以说：127.0.0.1是保留地址之一，只是被经常的使用，来检验本机TCP/IP协议栈而已。如果我们可以ping通的话，就说明：本机的网卡和IP协议安装都没有问题。（跟我们当前主机有没有联网没有一点关系）

#### (3)localhost

localhost是个域名，但是是个保留域名，是给回路网络接口（loopback）的一个标准主机名，相对应的IP地址为127.0.0.1（IPv4）和[::1]（IPv6）。它可以被配置为任意的IP地址（也就是说，可以通过hosts这个文件进行更改的），不过默认情况下都指向： 127.0.0.1。

​		本机IP，我们可以理解为本机有三块网卡，一块网卡叫做loopback（虚拟网卡），一块叫做ethernet（有线网卡），一块叫做wlan（你的无线网卡）。

**都是解析出来ip地址，并不会根据ip解析出域名**

- 根据主机名、域名解析出ip地址
- ip才是连接的关键

```java
package com.yalclass;

import org.junit.Test;

import java.net.InetAddress;
import java.net.UnknownHostException;
import java.util.Arrays;

public class SocketTest {
    
    //都是解析出来ip地址，并不会根据ip解析出域名

    @Test
    public void testInetAddress() throws UnknownHostException {
        //获得环回地址
        InetAddress address = InetAddress.getLoopbackAddress();
        System.out.println(address);

        //根据域名拿到ip地址，hostName就是域名
        InetAddress[] baidu = InetAddress.getAllByName("www.baidu.com");
        System.out.println(Arrays.toString(baidu));

        //根据localhost
        InetAddress[] localhosts = InetAddress.getAllByName("localhost");
        System.out.println(Arrays.toString(localhosts));

        //根据ip地址得到
        InetAddress[] allByName = InetAddress.getAllByName("127.0.0.1");
        System.out.println(Arrays.toString(allByName));

        //将环回地址保存进byte数组，然后使用byte数组进行获取——只能获得一个地址
        byte[] localHostByte = {127, 0, 0, 1};
        InetAddress byAddress = InetAddress.getByAddress(localHostByte);
        System.out.println(byAddress);

        //根据本机名获得网卡地址
        InetAddress[] 我s = InetAddress.getAllByName("景");
        System.out.println(Arrays.toString(我s));
    }
}
```

### 2、URL

- 使用URL进行下载，不仅可以下载网上的，还可以根据URL拿到本地的文件进行复制

#### (1)简介

​		URL（Uniform Resource Locator）中文名为统一资源定位符，咱们的网页地址也是一种URL。表示为互联网上的资源，如网页或者 FTP 地址。我们可以使用URL很方便的定位到一个资源，URL 可以分为如下几个部分。

```
protocol://host:port/path?query#fragment
```

protocol(协议)可以是 HTTP、HTTPS、FTP 和 File，port 为端口号，path为文件路径及文件名。

这个一个QQ的下载URL：

```
https://down.qq.com/qqweb/PCQQ/PCQQ_EXE/PCQQ2021.exe
```

URL 解析：

- 协议为(protocol)：https
- 主机为(host:port)：down.qq.com
- 端口号为(port) 443 ，以上URL实例并未指定端口，因为 HTTP 协议默认的端口号为443。
- 文件路径为(path)：/qqweb/PCQQ/PCQQ_EXE/PCQQ2021.exe

当然本地文件也可以使用URL来表示：

```java
file:///D:/a.txt
```



#### (2)URL 类方法

​		在java.net包中定义了URL类，该类用来处理有关URL的内容。对于URL类的创建和使用，下面分别进行介绍。

​		java.net.URL提供了丰富的URL构建方式，并可以通过java.net.URL来获取资源。

| 序号 | 方法描述                                                     |                                                              |
| :--- | :----------------------------------------------------------- | ------------------------------------------------------------ |
| 1    | public URL(String protocol, String host, int port, String file) throws MalformedURLException | 通过给定的参数(协议、主机名、端口号、文件名)创建URL。        |
| 2    | public URL(String protocol, String host, String file) throws MalformedURLException | 使用指定的协议、主机名、文件名创建URL，端口使用协议的默认端口。 |
| 3    | public URL(String url) throws MalformedURLException          | 通过给定的URL字符串创建URL                                   |
| 4    | public URL(URL context, String url) throws MalformedURLException | 使用基地址和相对URL创建                                      |

​		URL类中包含了很多方法用于访问URL的各个部分，具体方法及描述如下：

| 序号 | 方法                                                     | 描述                                    |
| :--- | :------------------------------------------------------- | --------------------------------------- |
| 1    | public String getPath()                                  | 返回URL路径部分。                       |
| 4    | public int getPort()                                     | 返回URL端口部分                         |
| 5    | public int getDefaultPort()                              | 返回协议的默认端口号。                  |
| 6    | public String getProtocol()                              | 返回URL的协议                           |
| 7    | public String getHost()                                  | 返回URL的主机                           |
| 8    | public String getFile()                                  | 返回URL文件名部分                       |
| 10   | public URLConnection openConnection() throws IOException | 打开一个URL连接，并运行客户端访问资源。 |

#### (3)从qqURL下载

```java
@Test
    public void testUrl() throws IOException {
        URL url = new URL("https://down.qq.com/qqweb/PCQQ/PCQQ_EXE/PCQQ2021.exe");
        //打开这个url
        URLConnection urlConnection = url.openConnection();
        //拿到流，抓到本地
        InputStream inputStream = urlConnection.getInputStream();
        OutputStream outputStream = new FileOutputStream("J:\\下载\\qq.exe");
        byte[] buffer = new byte[1024 * 1024];
        int len;
        while ((len = inputStream.read(buffer)) != -1){
            outputStream.write(buffer, 0, len);
        }
    }
```

### 3、ServerSocket 类的方法

​		服务器应用程序通过使用 java.net.ServerSocket 类以获取一个端口,并且侦听客户端请求。

​		ServerSocket 类有四个构造方法：

​		backlog是一个队列长度，我们可以简单的把他理解为最多允许多少个人排队握手。

| **序号** | **方法描述**                                                 |                                                              |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1        | public ServerSocket(int port)                                | 创建绑定到特定端口的服务器套接字                             |
| 2        | public ServerSocket(int port, int backlog)                   | 利用指定的 backlog 创建服务器套接字并将其绑定到指定的本地端口号 |
| 3        | public ServerSocket(int port, int backlog, InetAddress address) | 使用指定的端口、侦听 backlog 和要绑定到的本地 IP 地址创建服务器 |
| 4        | public ServerSocket() throws IOException                     | 创建非绑定服务器套接字                                       |



​		创建非绑定服务器套接字。 如果 ServerSocket 构造方法没有抛出异常，就意味着你的应用程序已经成功绑定到指定的端口，并且侦听客户端请求。

这里有一些 ServerSocket 类的常用方法：

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | public int getLocalPort()  返回此套接字在其上侦听的端口。    |
| 2        | public Socket accept()  侦听并接受到此套接字的连接。         |
| 4        | public void bind(SocketAddress host, int backlog)     将 ServerSocket 绑定到特定地址（IP 地址和端口号）。 |

------

​		

​		SocketAddress 指一个Socket的地址，它和InetAddress 不同，Socket网络地址除了需要主机名或IP之外，还需要一个用于通信的端口：

所以我们看到它的一个子类：InetSocketAddress的构造方法如下：

```java
public InetSocketAddress(int port) {
    this(InetAddress.anyLocalAddress(), port);
}


public synchronized InetAddress anyLocalAddress() {
    if (anyLocalAddress == null) {
        anyLocalAddress = new Inet4Address(); // {0x00,0x00,0x00,0x00}
        anyLocalAddress.holder().hostName = "0.0.0.0";
    }
    return anyLocalAddress;
}

-----------------------------------------------------------



public InetSocketAddress(InetAddress addr, int port) {
    holder = new InetSocketAddressHolder(
        null,
        addr == null ? InetAddress.anyLocalAddress() : addr,
        checkPort(port));
}
```





### 4、Socket 类的方法

java.net.Socket 类代表客户端和服务器都用来互相沟通的套接字。客户端要获取一个 Socket 对象通过实例化 ，而 服务器获得一个 Socket 对象则通过 accept() 方法的返回值。

Socket 类有五个构造方法.

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | public Socket(String host, int port) throws UnknownHostException, IOException. 创建一个流套接字并将其连接到指定主机上的指定端口号。 |
| 2        | public Socket(InetAddress host, int port) throws IOException 创建一个流套接字并将其连接到指定 IP 地址的指定端口号。 |
| 3        | public Socket(String host, int port, InetAddress localAddress, int localPort) throws IOException. 创建一个套接字并将其连接到指定远程主机上的指定远程端口。 |
| 4        | public Socket(InetAddress host, int port, InetAddress localAddress, int localPort) throws IOException. 创建一个套接字并将其连接到指定远程地址上的指定远程端口。 |
| 5        | public Socket() 通过系统默认类型的 SocketImpl 创建未连接套接字 |

当 Socket 构造方法返回，并没有简单的实例化了一个 Socket 对象，它实际上会尝试连接到指定的服务器和端口。

下面列出了一些感兴趣的方法，注意客户端和服务器端都有一个 Socket 对象，所以无论客户端还是服务端都能够调用这些方法。

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | **public void connect(SocketAddress host, int timeout) throws IOException** 将此套接字连接到服务器，并指定一个超时值。 |
| 2        | **public InetAddress getInetAddress()**  返回套接字连接的地址。 |
| 3        | **public int getPort()** 返回此套接字连接到的远程端口。      |
| 4        | **public int getLocalPort()** 返回此套接字绑定到的本地端口。 |
| 5        | **public SocketAddress getRemoteSocketAddress()** 返回此套接字连接的端点的地址，如果未连接则返回 null。 |
| 6        | **public InputStream getInputStream() throws IOException** 返回此套接字的输入流。 |
| 7        | **public OutputStream getOutputStream() throws IOException** 返回此套接字的输出流。 |
| 8        | **public void close() throws IOException** 关闭此套接字。    |

### 5、客户端和服务器进行通信



```java
@Test
    public void testServerSocket() throws IOException {
        //创建服务器插口
        ServerSocket server = new ServerSocket();
        //绑定端口——本机是服务器，所以创建的端口可以省略地址
        server.bind(new InetSocketAddress(8888));
        //监听端口
        Socket accept = server.accept();
        InputStream inputStream = accept.getInputStream();
        byte[] buffer = new byte[1024 * 1024];
        int len;
        while((len = inputStream.read(buffer)) != -1){
            System.out.println(new String(buffer, 0, len));
        }
        inputStream.close();
        accept.close();
    }
    @Test
    public void testUserSocket() throws IOException {
        //创建用户插板
        Socket socket = new Socket();
        //与服务器进行连接——因为连接的服务器不一定是本机，所以需要传入地址，使用的是InetAddress的静态方法获得环回地址
        socket.connect(new InetSocketAddress(InetAddress.getLoopbackAddress(),8888));
        OutputStream outputStream = socket.getOutputStream();
        outputStream.write("hello world".getBytes());

        //关闭资源
        outputStream.close();
        socket.close();
    }
```

### 6、UDP的实现

- 客户端端口创建的时候可以不确定端口号，但是需要确定发送的端口号；
- 服务端创建的时候必须确定端口号，不然接收不到信息

```java
//客户端实现udp
    @Test
    public void testUdpUser() throws IOException {
        //创建客户端端口
        //客户端会随机的分配ip
        DatagramSocket socket = new DatagramSocket();

        String str = "hello udp!";
        //创建一个数据包传输包裹——需要传输的数据，从0开始，到len，传入的目的地址
        DatagramPacket packet = new DatagramPacket(
                str.getBytes(), 0, str.getBytes().length,
                new InetSocketAddress(InetAddress.getByName("localhost"), 8080)
        );
        socket.send(packet);
        socket.close();
    }

    //服务端实现udp
    @Test
    public void testServerUdp() throws IOException {
        //创建服务器端口
        //创建接收端的时候要确定端口
        DatagramSocket socket = new DatagramSocket(8080);

        //创建接收的数据包
        byte[] buffer = new byte[1024];
        DatagramPacket packet = new DatagramPacket(
                buffer, 0, buffer.length
        );

        //阻塞，等待别人发消息
        socket.receive(packet);
        System.out.println(new String(packet.getData(), 0, packet.getLength()));
        socket.close();
    }
```

### 7、实现聊天

```java
client中的方法
////////////////
//给其他用户发消息
    private static void sendToFriend(String username, OutputStream outputStream, InputStream inputStream) {

        //先输入目标的名字
        System.out.print("请输入朋友的名字：");
        String friendName = ScannerUtils.scannerStr();
        boolean flag = true;
        while (flag) {
            //输入自己需要传递的信息
            System.out.print(username + "：");
            String msgConstant = ScannerUtils.scannerStr();
            if ("bye".equals(msgConstant)) {
                flag = false;
            }
            WriteMessage.writer(outputStream, new Message(MassageType.TO_FRIEND, msgConstant, username, friendName));
        }
    }
    

//
package com.ydlclass;

import com.ydlclass.constant.Constant;
import com.ydlclass.constant.MassageType;
import com.ydlclass.util.ReadMessage;
import com.ydlclass.util.WriteMessage;

import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.util.Optional;

public class ServerThread extends Thread {
    public Socket socket;

    public ServerThread() {
    }

    public ServerThread(Socket socket) {
        this.socket = socket;
    }

    @Override
    public void run() {
        try (
                InputStream inputStream = socket.getInputStream();
                OutputStream outputStream = socket.getOutputStream()
        ) {
            while (true) {
                //获得端口的输入流，然后使用工具类进行读
                Optional<Message> readMsg = ReadMessage.read(inputStream);
                if (readMsg.isPresent()) {
                    Message mms = readMsg.get();
                    switch (mms.getType()) {
                        case MassageType.LOGIN:
                            toLogin(socket, outputStream, inputStream, mms);
                            break;
                        case MassageType.TO_SERVER:
                            sendToClient(outputStream, mms);
                            break;
                        //服务其拿到消息，然后根据消息里面的要求进行传递
                        case MassageType.TO_FRIEND:
                            sendToTarget(mms);
                            break;
                        case MassageType.TO_ALL:
                            sendToAll(inputStream, outputStream, mms);
                            break;
                        default:
                            break;

                    }
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }


    }


    /**
     * 服务器收到用户的消息之后进行回应
     * 先输出消息的内容，然后给用户端回应一个消息
     * @param outputStream
     * @param mms
     */
    private  void sendToClient(OutputStream outputStream, Message mms) {
        System.out.println(mms.getUsername() + ":" + mms.getContent());
        WriteMessage.writer(outputStream, Constant.SERVERTOCLIENTMSG);
    }

    private  void sendToTarget(Message mms) {
        //找到目标
        String friendName = mms.getFriendName();
        //找到目标的socket——好友的端口
        Socket targetSocket = Constant.USERS_SOCKET.get(friendName);
        try (
             OutputStream outputStream1 = targetSocket.getOutputStream()
        ){
            //向目标传递信息
            WriteMessage.writer(outputStream1,mms);
            //
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
    //222222
    //向指定用户发送
    private void sendToTarget(Message mms) throws IOException {
        //找到目标
        String friendName = mms.getFriendName();
        //找到目标的socket——好友的端口
        Socket targetSocket = Constant.USERS_SOCKET.get(friendName);
        //连接好友的端口
        OutputStream outputStream = targetSocket.getOutputStream();
        //向目标传递信息
        WriteMessage.writer(outputStream, mms);
    }

    private  void sendToAll(InputStream inputStream, OutputStream outputStream, Message mms) {

    }


    //登录
    private  void toLogin(Socket accept, OutputStream outputStream, InputStream inputStream, Message msg) {
        //如果拿到的消息为空或者密码不对或者用户名为空就给客户端发送一个消息
        if (msg.getUsername() == null || !Constant.DEFAULT_PASSWORD.equals(msg.getPassword())) {
            WriteMessage.writer(outputStream,
                    new Message(MassageType.FROM_SERVER, Constant.FAIL, "server"));
        }
        //如果登陆成功也给客户端回一个消息
        else {
            Constant.USERS_SOCKET.put(msg.getUsername(), accept);
            WriteMessage.writer(outputStream,
                    new Message(MassageType.TO_SERVER, Constant.SUCCESS, "server"));
            System.out.println(msg.getUsername() + "登陆成功");
        }
    }
}

```

四、大作业

1. 分清楚消息发送的方向
2. 构造器分清楚
3. 不能随便关流
4. 服务器绑定端口，客户端连接端口



# 第十八章 NIO

除了NIO还有AIO

## 一、NIO简介

服务端有个阻塞方法，一个线程执行到这里的时候，等待输入，就会阻塞这个线程，如果线程挂起(内核态和用户态之间的切换)或者自旋都会造成资源浪费

BIO：同步(代码一行一行的执行)并阻塞

NIO：同步非阻塞

`一个线程去客户家里，客户不在，需要三天才能回来，在客户家里睡了三天——阻塞，资源浪费——BIO`

`一个线程去第一个客户家里，客户不在，三天之后才能回来，这三天先去访问别的客户，先处理别的事情，三天之后再来——NIO`

1）Java BIO ： 同步并阻塞(传统阻塞型)，服务器实现模式为一个连接一个线程，即客户端有连接请求时服务器端就需要启动一个线程进行处理，如果这个连接不做任何事情会造成不必要的线程开销。

![image-20210916114632687](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916114632687.png)



2）Java NIO ： 同步非阻塞，服务器实现模式为一个线程处理多个请求(连接)，即客户端发送的连接请求都会注册到多路复用器上，多路复用器轮询到连接有I/O请求就进行处理。

![image-20210916114642170](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916114642170.png)

- 每个客户端连接上操作系统，都会创建一个fd(文件描述符)，每个文件描述符，客户端和文件描述符之间都是有通道(Channel)的,Channel是双向的。
- 当文件描述符有了文件，就调用Selector去看
- Channel相当于火车轨道——跑Buffer的，Buffer相当于火车货箱——传数据。

## 二、操作系统的几个概念

### 1、内核态和用户态

> 为什么要有用户态和内核态？

​	限制不同程序之间的访问能力，防止他们获得别的程序的内存数据，或者获得外围设备的数据，并发送到网络。

> 什么时候发生用户态和内核态的切换？

​	【用户态在需要申请外部资源的时候会切换至内核态】，比如执行系统调用、发生中断、异常等，内核态执行完成之后会返回用户态。

### 2、系统调用

- 有系统调用的API；
- 系统调用是操作系统开发的接口，开发者可以使用【系统调用】获取系统资源。就是操作系统的代码开放了一些接口让你使用，比如创建个文件，读取个文件。

> 常见的系统调用如下：

1、和进程、线程相关   fork创建一个子进程

2、文件相关的   creat chmod chown   read从一个文件描述符中读取内容   write——向一个文件描述符中写入内容  close——关闭文件描述符

3、设备相关的   read write

4、信息相关的  get...

5、通信相关的  pipe 

> 文件描述符

```java
int open(const char *pathname, int flags);
```

这个系统调用函数有一个int类型的返回值，这个就是文件描述符。

### 3、系统中断

![image-20210916113109617](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916113109617.png)

> 中断的分类：

【中断源】是指能够引起中断的原因。一台【处理器】可能有很多中断源,但按其性质和处理方法,大致可分为如下五类：

1. 机器故障中断，比如掉电。
2. 程序性中断。现行程序本身的异常事件引起的，可分为以下三种：一是程序性错误，非法操作和除数为零等；二是产生特殊的运算结果，例如定点溢出；三是程序出现某些预先确定要跟踪的事件，跟踪操作主要用于[程序调试](https://baike.baidu.com/item/程序调试)。有些机器把程序性中断称为“异常”，不称为中断。
3. IO－【输出设备】中断，IO中断。
4. 外中断。来自控制台【中断开关】、计时器、时钟或其他设备，这类中断的处理较简单，实时性强。
5. 调用管理程序。用户程序利用专用指令“调用管理程序”发【中断请求】，是用户程序和操作系统之间的联系桥梁。



> 系统中断有什么好处：

1、分时操作，解决CPU的快速处理和慢速IO设备的问题。

2、实时处理，word中可以一边打字一边做拼写检查。

3、故障处理，会优先处理故障。



### 4、DMA

​		DMA(Direct Memory Access，直接存储器访问) ，它允许不同速度的硬件装置来沟通，而不需要依赖于[ CPU ](https://baike.baidu.com/item/ CPU /120556)的大量中断负载。否则，CPU 需要从来源把每一片段的资料复制到暂存器，然后把它们再次写回到新的地方。在这个时间中，CPU 对于其他的工作来说就无法使用。

​		当CPU需要访问外设（磁盘、网卡、usb）的数据时，将任务丢给DMA，有DMA负责利用总线将数据先拷贝到内存，DMA传输前，CPU要把总线控制权交给DMA控制器，而在结束DMA传输后，DMA控制器应立即把总线控制权再交回给CPU。传输结束后，发出中断信号，通知CPU。

![image-20210916103731515](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916103731515.png)

- DMA与其他设备相连，如果程序需要哪个设备的信息，就发送消息给DMA，让DMA去获取信息，DMA拿到之后，放到内存，然后给程序发送一个中断信号，然后程序去拿DMA取得的信息。

### 5、数据结构位图bitmap：

有一个场景：需要你统计你的同事的一个月的打卡记录。

你要怎么做，创建三十几个变量，0代表没打卡，1代表已打卡？

事实上我们使用一个int能表示：

```
11111111 10101111 11111111 11111110
```

​		一个int四个字节，就是三十二位，从第0位开始算第一天的打卡记录，那么有三十二位足够了，因为一个月最多也就31天。

​		我们能很简单的看出他第10天和12天没有打卡。



### 

## 三、NIO相关的系统调用

- 程序和很多用户端口连接，连接一个端口就会把文件操作符添加进bitmap中，用户通知只能通知到用户态， 但是用户接收消息的时候会中断，但是中断只能通知到内核，所以我们把bitmap拷贝到服务器中。
- 服务器得到bitmap，就会把这些文件描述符找出来，遍历一遍，看看有哪些地方过来数据，然后中断，通知操作系统拿到数据，操作系统发送数据到客户端。这个过程调用了`select系统操作`select的返回值是一个int，内容是已经有几个文件描述符有了新的状态或者已经发生了。

### 1、select系统调用

- 每次传递的bitmap一定是一个长度为1024的数组
- 每次查找都是所有的文件描述符遍历

​		select系统调用有一个重要参数，为fd文件描述符集合，即你要监听哪些文件描述符（哪些连接），这个文件描述符集合rset用一个bitmap位图表示，位图大小为1024，即最多只能监听1024个客户端连接。

​		当发起系统调用时，会将rset拷贝到内核态，然后内核态监听有没有数据可以处理，监听的所有文件描述符都没有数据的话会一直阻塞，直到有数据时，将有数据的fd索引置一，然后返回给用户态

Select缺点：

- 位图大小默认1024，有上限。

- 每次都需要创建一个文件描述符位图并拷贝到内核态。

  

```
int select(int nfds, fd_set *readfds, fd_set *writefds,
                  fd_set *exceptfds, struct timeval *timeout);

```

1. nfds：要检测的文件描述符数量，最大文件描述符加1。
2. readfds：指定了被读监控的文件描述符集；
3. writefds：指定了被写监控的文件描述符集；
4. exceptfds：指定了被例外条件监控的文件描述符集；
5. timeout：超时时间。

readfds是个长度为1024的bitmap。我们都知道fd文件描述符有一个序号，

如果现在我监听3，6，8号的fd，那么位图就是：

```
...10100100
```

那么select的具体流程是什么呢？

1、应用程序创建socket，生成文件描述符，并生成bitmap，使用hash的方式将bitmap的对应位置置一。

2、执行系统调用，将bitmap拷贝至内核空间，根据bitmap遍历对应的文件描述符，一旦有事件产生就返回。

3、用户程序遍历文件描述符，处理请求。

4、应用程序不停的调用select即可。

![image-20210916130932678](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916130932678.png)

select模型已经很不错了，但是依然有不足的地方：

1. bitmap位图上限是1024，所以能监控的fd最多也就这么多。

2. fset位图不可重用，每次赋值全部清零，状态全部丢失。

3. fset位图需要不断的进行用户空间到内核空间的拷贝。

4. 每次查找时间复杂度都是O(n)。

   ​	用户关心的文件描述符有100个，但是select返回有3个文件描述符有状态了，但是用户仍然需要将关心的100个文件遍历一次。

   ​	select只能告诉程序有几个文件描述符发生状态了，并不能说哪个文件描述符发生状态。

> 和accept的区别：如果有一个用户端与服务端连接，accept开始监听，如果有新的用户需要连接就不可以，因为accept是单线程的，但是使用selece就不一样

```java
while(true){
    select(bitmap);
    bit...  //获得需要关心	的文件操作符
    for(bit){
        对文件操作符进行遍历，拿到数据
    }
}
```

### 2、Poll系统调用

​		Poll工作原理与Select基本相同，不同的只是将位图数组改成数组，也有资料说是链表，没有了最大连接数1024的限制，依然有fd集合的拷贝和O(n)的遍历过程。

![image-20210916143032566](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916143032566.png)



```
 int poll(struct pollfd *fds, nfds_t nfds, int timeout);
```

这个系统调用的

1. fds：存放需要被检测状态的套接字描述符，与select不同（select在调用之后会清空这个数组），每当调用这个数组，系统不会清空这个数组，而是存放revents状态变化描述符变量，这样才做起来很方便。

2. nfds：用于标记数组fd中struct pollfd结构元素的总数量。

3. timeout：是超时时间。

4. 返回值大于零表示成功，返回满足条件的文件描述符的个数

   返回值等于零，表示超时。

   返回值等于-1 发生错误，比如描述符不合法，接受到中断信号，内存不足

被检测的套接字使用结构体封装，如下：

```c++
struct pollfd {
    int   fd;         /* file descriptor */
    short events;     /* requested events */
    short revents;    /* returned events */
};

```

> pollfd

1. fd       文件描述符
2. events   请求的事件
3. revents  返回的事件

> 事件的类型比如： 

1. pollin表示文件有数据来、文件描述符可读
2. pollout表示文件可写
3. pollerr表示错误发生  



poll的优势：

1、大量的 fd的数组被整体复制于用户态和内核地址空间之间，而不管这样的复制是不是有意义。

 2、 可重用



### 3、Epoll系统调用

​		为解决fd集合拷贝的问题，epoll采用用户态和内核态共享epoll_fds集合。当调用epoll_wait系统调用时，内核态会去检查有哪些fd有事件，检查完毕后会将共享的epoll_fds集合重排序，将有事件的fd放在前面，并返回有事件的fd个数。

​		客户端收到返回的个数，就不需要全部遍历，而是直接处理fd。

```c
1、int epoll_create(int size);
//创建epoll
#注意：size参数只是告诉内核这个 epoll对象会处理的事件大致数目，而不是能够处理的事件的最大个数。在 Linux最新的一些内核版本的实现中，#这个 size参数没有任何意义。

2、int epoll_ctl(int epfd, int op, int fd, struct epoll_event *event);
//对fd进行监听，监听进刚才创建的epoll中
#epoll的事件注册函数，epoll_ctl向 epoll对象中添加、修改或者删除感兴趣的事件，返回0表示成功，否则返回–1，此时需要根据errno错误码##判断错误类型。

#它不同与select()是在监听事件时告诉内核要监听什么类型的事件，而是在这里先注册要监听的事件类型。


3、int epoll_wait(int epfd, struct epoll_event * events, int maxevents, int timeout);
//开始等待，监听中的哪个文件描述符发生事件了，发生事件了就准备返回
epoll_wait方法返回的事件必然是通过 epoll_ctl添加到 epoll中的。
#第一个参数是epoll_create()的返回值，
#第二个参数表示动作，用三个宏来表示：
#EPOLL_CTL_ADD：注册新的fd到epfd中；
#EPOLL_CTL_MOD：修改已经注册的fd的监听事件；
#EPOLL_CTL_DEL：从epfd中删除一个fd；
#第三个参数是需要监听的fd，第四个参数是告诉内核需要监听什么事


```

处理流程大致如下：

![image-20210916143428054](%E5%9B%BE%E7%89%87/javese%E5%85%83%E5%8A%A8%E5%8A%9B%E6%96%87%E4%BB%B6/nio.assets/image-20210916143428054.png)

> 1. 系统开始的时候会使用epoll_create在共享空间中创建红黑树
> 2. 每次创建一个用户，都会在将文件操作符epoll_ctl注册进共享空间中，形成红黑树，
> 3. 使用epoll_wait阻塞，等待系统调用
> 4. 进行系统调用的时候，系统内核会自动从红黑树中通过对应的文件描述符所指向的文件进行监听，如果监听到数据，就向程序返回一个数字(有数据的文件个数)

小案例：

```c
 #define MAX_EVENTS 10
struct epoll_event ev, events[MAX_EVENTS];
int listen_sock, conn_sock, nfds, epollfd;

/* Code to set up listening socket, 'listen_sock',
              (socket(), bind(), listen()) omitted */
// 招一个小弟
epollfd = epoll_create1(0);
if (epollfd == -1) {
    perror("epoll_create1");
    exit(EXIT_FAILURE);
}

ev.events = EPOLLIN;
ev.data.fd = listen_sock;

// 谁有什么事先和小弟说
if (epoll_ctl(epollfd, EPOLL_CTL_ADD, listen_sock, &ev) == -1) {
    perror("epoll_ctl: listen_sock");
    exit(EXIT_FAILURE);
}

for (;;) {
    // 老板在那里等小弟的回应，有回应就去处理
    nfds = epoll_wait(epollfd, events, MAX_EVENTS, -1);
    if (nfds == -1) {
        perror("epoll_wait");
        exit(EXIT_FAILURE);
    }

    for (n = 0; n < nfds; ++n) {
        if (events[n].data.fd == listen_sock) {
            conn_sock = accept(listen_sock,
                               (struct sockaddr *) &addr, &addrlen);
            if (conn_sock == -1) {
                perror("accept");
                exit(EXIT_FAILURE);
            }
            setnonblocking(conn_sock);
            ev.events = EPOLLIN | EPOLLET;
            ev.data.fd = conn_sock;
            if (epoll_ctl(epollfd, EPOLL_CTL_ADD, conn_sock,
                          &ev) == -1) {
                perror("epoll_ctl: conn_sock");
                exit(EXIT_FAILURE);
            }
        } else {
            do_use_fd(events[n].data.fd);
        }
    }
}


```

1. 重排相当于置位，每次会把有事件发生的fd排在前边
2. 没有靠背开销，共享内存。
3. o(1)复杂度。



## 四、Java中实现NIO

Buffer是一个抽象类，尝试观看源代码；

​	IntBuffer创建的时候不能new，是使用IntBuffer的静态方法 `allocate(参数)`申请参数大小的空间`put()`可以传递数组和数字

`使用Buffer的时候注意指针回调， Flip()`

### 1、Buffer

#### (1)、创建一个Buffer，然后遍历

```java
 @Test
    public void testIntBuffer(){
        IntBuffer buffer = IntBuffer.allocate(10);
        buffer.put(new int[]{1, 2, 3, 4, 5});
        //拨回指针到数组头部
        //如果不调回去，就输出的都是0，因为指针问题
        buffer.flip();
        for (int i = 0; i < 5; i++) {
            //buffer是一个指针，刚开始指向的是数组的头部，添加一个buffer往后挪一位
            System.out.println(buffer.get());
        }
    }
```

### 2、Channel

#### (1)、创建一个连接文件的通道

```java
@Test
    public void testChannel() throws IOException {
        FileOutputStream outputStream = new FileOutputStream("J:\\code\\File\\a.txt");
        /**
         * 使用allocate申请空间之后put传入数组或者直接使用wrap包装一个
         * 如果使用allocate()，然后使用put进行添加之后，需要将指针重置一下，不然就是从指针现在的位置开始添加
         * 如果直接使用wrap进行包装的时候就不会出现这种问题，因为wrap是直接将字符串包装成一个ByteBuffer了，没有使用put，没有动指针
         */

        /*ByteBuffer buffer = ByteBuffer.allocate(10);
        buffer.put(new byte[]{1, 2, 3, 4, 5});*/
        ByteBuffer buffer = ByteBuffer.wrap("hello nio".getBytes());
        //拿到一个通向文件的通道
        FileChannel channel = outputStream.getChannel();
        channel.write(buffer);

        outputStream.close();
        channel.close();
    }
```

### 3、创建nio服务端

```java
package com.ydlclass;

import java.io.IOException;
import java.net.InetSocketAddress;
import java.nio.ByteBuffer;
import java.nio.channels.*;
import java.util.Iterator;
import java.util.Set;

public class NioServer {
    public static void main(String[] args) throws IOException {
        //创建连接服务器通道
        //创建好Channel后系统就有一个文件描述符连接这个Channel
        //将创建好的Channel注册给selector
        ServerSocketChannel server = ServerSocketChannel.open();
        //-将Channel配置成非阻塞IO-必须写
        server.configureBlocking(false);
        server.bind(new InetSocketAddress(6666));

        //创建一个IO多路复用选择器
        Selector selector = Selector.open();

        //注册Channel，注册进哪个selector，这个服务器关心的是连接，有哪写客户端想连接，然后告诉selector
        server.register(selector, SelectionKey.OP_ACCEPT);

        while(true){
            //多路复用检查器进行系统调用，是个阻塞的方法
            //0——超时   -1——错误
            //可以传进参数为等待的时间(超时时间)，如果不写就是一直等待
            selector.select(1000);
            //如果进行到这里，一定发生了事件，有可读可写可连接的Channel
            Set<SelectionKey> selectionKeys = selector.selectedKeys();
            //拿到所有事件之后进行迭代遍历
            Iterator<SelectionKey> iterator = selectionKeys.iterator();
            while (iterator.hasNext()){
                //拿到有事件的通道
                SelectionKey selectionKey = iterator.next();
                if (selectionKey.isAcceptable()){
                    System.out.println("有人连接了");
                    //有人请求连接，然后使用数据库连接
                    SocketChannel accept = server.accept();
                    accept.configureBlocking(false);
                    //绑定选择器，对读感兴趣，给通道绑定一个Buffer
                    accept.register(selector, SelectionKey.OP_READ, ByteBuffer.allocate(1024));
                }
                if (selectionKey.isReadable()){
                    //如果事件为读，就拿到这个通道
                    SocketChannel channel = (SocketChannel)selectionKey.channel();
                    //先拿到buffer
                    ByteBuffer attachment = (ByteBuffer)selectionKey.attachment();
                    channel.read(attachment);
                    System.out.println(new String(attachment.array(), 0, attachment.position()));
                    attachment.clear();
                }
                iterator.remove();
            }
        }
    }
}

```

### 4、创建用户端口

```java
package com.ydlclass;

import java.io.IOException;
import java.net.InetSocketAddress;
import java.nio.ByteBuffer;
import java.nio.channels.SocketChannel;
import java.util.Scanner;

public class NioClient {
    public static void main(String[] args) throws IOException {
        SocketChannel socketChannel = SocketChannel.open();
        socketChannel.connect(new InetSocketAddress(6666));
        socketChannel.configureBlocking(false);
        if (socketChannel.finishConnect()){
            while (true){
                Scanner scanner = new Scanner(System.in);
                String next = scanner.next();
                socketChannel.write(ByteBuffer.wrap(next.getBytes()));
            }
        }

    }
}

```















以及是什么原因产生了异常。