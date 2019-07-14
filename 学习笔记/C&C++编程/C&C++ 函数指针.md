> 函数指针是指向函数的指针变量。 因此“函数指针”本身首先应是指针变量，只不过该指针变量指向函数。这正如用指针变量可指向整型变量、字符型、数组一样，这里是指向函数。如前所述，C在编译时，每一个函数都有一个入口地址，该入口地址就是函数指针所指向的地址。有了指向函数的指针变量后，可用该指针变量调用函数，就如同用指针变量可引用其他类型变量一样，在这些概念上是大体一致的。函数指针有两个用途：调用函数和做函数的参数。

### 简单应用
```
#include <iostream>
using namespace std;

//使用函数重载定义三个同名函数
void test(void){cout << "Nothing" << endl;}
void test(int a){cout << a << endl;}
void test(int a, int b){cout << a << "," << b << endl;}

int main(void)
{
    int a = 1000, b = 2000;
    test();
    test(a);
    test(a,b);
    //定义三个指向不同类型的函数指针
	void (*pf1)(void);
	void (*pf2)(int);
	void (*pf3)(int, int);
    //虽然名称相同，但是实质是三个不同的函数
	pf1 = test;
	pf2 = test;
	pf3 = test;

	cout << pf1 << endl;
	cout << pf2 << endl;
	cout << pf3 << endl;
}
```
输出
```
Nothing
1000
1000,2000
00B4128F
00B410F0
00B410E1
```
### 与typedef一起使用
```#include <iostream>
using namespace std;

void test(void){cout << "Nothing" << endl;}
void test(int a){cout << a << endl;}
void test(int a, int b){cout << a << "," << b << endl;}

int main(void)
{
    int a = 1000, b = 2000;
    test();
    test(a);
    test(a,b);
    //注意一下typedef搭配函数指针使用的语法
	typedef void (*PF1)(void);
	typedef void (*PF2)(int);
	typedef void (*PF3)(int, int);

	PF1 pf1 = test;
	PF2 pf2 = test;
	PF3 pf3 = test;

	cout << pf1 << endl;
	cout << pf2 << endl;
	cout << pf3 << endl;
}

```
输出
```
Nothing
1000
1000,2000
00CE128F
00CE10F0
00CE10E1
```

`2019-07-11`
