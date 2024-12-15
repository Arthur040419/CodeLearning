# C++碎碎念

## 相对路径的使用

要写一个程序，很难离开文件的读写，所以学会使用相对路径是很有必要的。

### 参考文章

[什么是相对路径？相对路径的具体写法和用法 - 司砚章 - 博客园](https://www.cnblogs.com/jgg54335/p/14787211.html)

#### 几种相对路径的表示

在相对路径表示中，`.`表示当前目录，`..`表示上级目录，`/`表示分隔目录

`./`开头表示当前目录，可以省略不写

`../`开头表示上级目录

`../../`开头表示上上级目录

`/`开头表示根目录

## C++ main函数的参数

### 参考文章

[C++ main函数的参数 - Jisongxie - 博客园](https://www.cnblogs.com/jisongxie/p/7892366.html)

#### 基本情况

main函数的参数可以没有，也可以有，但有只能有两个，一般参数就按照下面的方式来定义

```
int main(int argc, char* argv[])
```

#### 具体含义

`argc`代表的是该程序的参数数量（包括程序本身的名称），`argv`代表的是执行程序时传入程序的参数，一般`argv[0]`是程序名，`argv[1]~argv[n]`是程序里定义的变量

例如：我有一个写好的C++程序 `years.cpp`，它编译后会生成一个`years.exe`的可执行文件，假如这个程序里面定义的参数有`year old`，那么这个时候，`argc`就是3，`argv[0]`就是`years.exe`，`argv[1]`就是`year`,`argv[2]`就是`old`。

#### 为啥会存在参数这一东西

首先`main`函数是不能被其他函数调用的，所以不可能会从`mian`函数中得到返回值，所以这个参数肯定不是为了用来从`main`函数中得到返回值的。`main`函数的参数是从操作系统的命令行上获取的，所以就像上面说的那样，如果有一个years.exe可执行文件，我们可以在命令行里输入以下命令来执行程序

```
years.exe 2004 20
```

所以目前看来这些参数存在的意义我只看到了1个，就是如果有这些参数，你就可以通过命令行来执行这个程序，这具体又有啥用，我现在也不得而知。

## VisualStudio运行项目切换

我在编写多个项目时遇到了一个问题，就是当我运行项目时，不管运行哪一个，它运行的都是第一个编译运行的项目，原因是想运行其他项目时没有将启动项切换到对应的项目（就是个小问题）

切换方法很简单，只要右键想要切换的那个项目，找到`设为启动项`这一选项就行



## 求Π（就是那个圆周率）

咱一般碰到的也就是拿Π去求其他东西，这里放过来要我求Π，我还真不会

#### 公式

利用反正切函数

`*π*=16⋅arctan(1/5)−4⋅arctan(1/239)`

这个公式咋来的就不管了，要真去追究那就为难我了

#### 重点是编写反正切函数

反正切函数的级数展开如下

![{FB780CBE-F92F-49E8-9342-657FF4B2AAA9}](D:\CodeTool\Code-Study\pictures\{FB780CBE-F92F-49E8-9342-657FF4B2AAA9}.png)

也可用`tail%4==1`来确定哪一项要加还是减

```c++
double arctan(double x){
    double head = x;	//head为每一项的分子
    int tail = 1;	//tail为每一项的分母
    double art = 0;		//art为最终求出来的反正切的值
    while(head/tail > 1e-15){ //模拟级数展开，一直展开，直到展开到那一项小于1e-15
        art = tail%4 == 1?art+head/tail:art-head/tail;		//根据tail判断每一项是加进去还是减去
        head = head*x*x;		//接着写出下一项
        tail +=2;
        
    }
    return art;	//知道出现比1e-15小的项就退出循环并输出结果
}
```

## 枚举类

### 参考文章

[【C++】C++中的枚举enum类型使用详解_c++ enum-CSDN博客](https://blog.csdn.net/qq_35902025/article/details/127567837)



## 计算组合数(C(n,k))

#### 公式

数学上计算n个里面选k个，即计算组合数有一个公式

![{03A4FA68-DA62-4FA0-9A78-7AE93ECC2B10}](D:\CodeTool\Code-Study\pictures\{03A4FA68-DA62-4FA0-9A78-7AE93ECC2B10}.png)

#### 方法一：递归函数

```c++
int f(n,k){
    if(n==k||k==0){		//从n个里面选n个和从n个里面选0个可以直接得出结果
        return 1;
    }
    else{
        return f(n-1,k-1)+f(n-1,k);
    }
}
```

#### 方法二：动态规划(待补充)





## 结构体大小计算

### 参考文章：

[C++ sizeof(struct)计算结构体大小_sizeof struct-CSDN博客](https://blog.csdn.net/GL3_24/article/details/100170043)

#### 误区

结构体的大小计算不是简单的把成员变量的大小加起来就行，为了提高内存访问效率，结构体大小的计算会考虑一个`内存对齐`的因素

#### 正确方法

首先，要知道偏移量是什么，在结构体中，偏移量就是成员变量开始地址离整个结构体开始地址的距离，举个例子

```c++
struct student {
  int num;
  char name[20];
  char gender;
};

//在这里，num的偏移量就是0，因为它是第一个成员变量，它的首地址就是整个结构体的首地址
//name[20]的偏移量就是4，因为它前面的成员变量的大小是4，所以它离整个结构体的首地址是要加上前面变量的大小
//gender的偏移量是24
//最终整个结构体的偏移量就是最后一个变量的偏移量+最后一个变量的大小，所以最后的出结构体的偏移量就是25
```

根据偏移量可以计算出不考虑内存对齐的结构体的正确大小，但我们要考虑内存对齐就要在这个计算出的大小的基础上在运用两个原则

```
//原则1
结构体变量中成员的偏移量必须是成员大小的整数倍（0被认为是任何数的整数倍）（我这里暂时把数组变量的大小看成它一个元素的大小，应该是这样的） 
//原则2
结构体大小必须是所有成员大小的整数倍，也即所有成员大小的公倍数。
运用以上原则的到的结构体大小就是28
```



## 随机数

### 参考文章

[rand()和srand()的使用方法和二者之间的关系_rand函数与srand函数的关系-CSDN博客](https://blog.csdn.net/ThinPikachu/article/details/110491159)



#### 头文件

`#include<cstdlib>`



#### 关键函数

```c++
unsigned seed;
srand(seed);			//初始化随机数种子
rand()					//根据随机数种子生成随机数，伪随机，种子不同，生成的随机数顺序就不同，种子相同，生成的随机数顺序就相同
```



## 内联函数（提高运行效率）

### 参考文章

[【C++】C++中内联函数详解（搞清内联的本质及用法）-CSDN博客](https://blog.csdn.net/qq_35902025/article/details/127912415)

#### 作用

在编译时直接用函数在调用函数的那个位置进行替换，省去了函数调用的时间，提高了程序运行效率

#### 定义

```c++
//只需在函数定义和声明前加上inline
//声明
inline double CalArea(double radius);
//定义
inline double CalArea(double radius){
    return 3.14*radius*radius;
}
```





## 类前向声明

### 参考文章

**[C++ 类的前向声明的用法 - 王陸 - 博客园](https://www.cnblogs.com/wkfvawl/p/10801725.html)**

#### 作用

类应该是先定义再使用，但再C++的复杂程序中，难免出现类与类之间相互引用的情况，这种情况叫循环依赖

```c++
class A{
  public:
    B b;		//定义一个B类对象
};

class B{
    public:
    A a;		//定义一个A类对象
}

//这两个类，不管谁定义在前，都会出现编译错误
```

为了解决这个问题，我们就可以使用类前向声明，就是先告诉编译器，这是一个类，具体类的定义可以在其他地方再定义

```c++
class B;
class A{
  public:
    B* b;		//定义一个B类指针就行，这样编译器就可以知道这是一个类
};

class B{
    public:
    A* a;
}
```

## 静态成员变量

#### 定义

只能在类外进行初始化，所有生成的类共同维护这个静态成员变量

#### 例子

```c++
#include<iostream>
using namespace std;
class point {
public:
	point(int xx = 0, int yy = 0) {
		x = xx;
		y = yy;
		countP++;
	}
	point(point& p) {
		x = p.x;
		y = p.y;
		countP++;
	}
	int getx() {
		return x;
	}
	int gety() {
		return y;
	}
	int getc() {
		return countP;
	}
private:
	int x;
	int y;
	static int countP;		//静态数据成员必须在类外定义
};

int point::countP = 0;
int main(int argc, char const* argv[]) {
	point A(4, 5);			//每建立一个point，countP就加1，这个countP是所有point对象都拥有的
	cout << "point A," << A.getx() << "," << A.gety() << endl;
	cout << A.getc() << endl;
	point B(A);
	cout << "point B," << B.getx() << "," << B.gety() << endl;
	cout << B.getc() << endl;
}
```

## 静态成员函数

#### 定义

静态成员函数只能调用属于自己类的静态成员变量和其他静态成员函数

类外代码可以使用类名和作用域操作符来调用静态函数





## 创建动态二维数组

### 参考文章

[C++建立动态二维数组_c++动态声明二维数组-CSDN博客](https://blog.csdn.net/longshengguoji/article/details/11131365)

#### 方法

使用数组指针，假设我要建立一个n维的动态的二维数组dp，我可以先创建一个数组指针dp，然后为这个数组指针dp的每一个元素分配一个一维数组

```c++
//创建数组指针dp
int **dp=new int*[n];
//为数组指针dp的每一个元素分配一个一维数组
for(int i=0;i<n;i++){
    dp[i]=new int[n];
}

```

#### 删除动态二维数组

这样创建的动态二维数组不能直接用`delete dp`来删除。

正确的删除方法是：先删除dp的每一个数组元素，然后在删除dp

```c++
//先删除dp的每一个元素
for(int i=0;i<n;i++){
    delete dp[i];
    dp[i]=NULL;
}
//最后删除dp
delete dp;
dp=NULL
```

## 求数组的最大值或最小值（包括二维数组）

### 参考文章

[c++中数组或vector求最大值最小值的库函数_c++ vector max-CSDN博客](https://blog.csdn.net/Leiroy/article/details/119333526)

#### 方法

需要用到头文件`#include<algorithm>`

使用以下两个函数来求数组最大值和最小值

```c++
#include<algorithm>
int a[5];		//假设有这样一个数组a
//最大值 max_element(int x,int y);			x,y为指定的范围，该函数返回指定数组范围内的最大值的地址
int maxvalue= *max_element(a,a+5);			//返回数组a的最大值
//最小值 min_element(int x,int y)
int minvalue+ *min_element(a,a+5);
```



上面是一维数组，那二维数组咋办呢

```c++
#include<algorithm>
int a[10][10];
//假设我想求二维数组某一行的最大值
int maxvalue= *max_element(a[10],a[10]+10);		//求二维数组最后一行的最大值
```

