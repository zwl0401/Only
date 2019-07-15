# 重载 overload
`函数名字一样，但是本质上还是可以根据入参的不同加以区分`
> 重载，简单说，就是函数或者方法有相同的名称，但是参数列表不相同的情形，这样的同名不同参数的函数或者方法之间，互相称之为重载函数或者方法。

> 重载只是一种语言特性，是一种语法规则，**与多态无关**，与面向对象也无关。

```c++
#include <iostream>
using namespace std;

void test(void) {cout << "Nothing" << endl;}
void test(int a) {cout << a << endl;}
void test(int a, int b) {cout << a << "," << b << endl;}

int main(void)
{
    int a = 1000, b = 2000;
    test();
    test(a);
    test(a,b);
}
```
输出
```
Nothing
1000
1000,2000
```

# 多态 Polymorphism

> 多态按字面的意思就是“多种状态”。在面向对象语言中，**接口的多种不同的实现方式**即为多态。
* ###  重写 overwrite
`重写的本质是子类成员函数隐藏父类成员函数`
> 是指派生类的函数屏蔽了与其同名的基类函数，规则如下：
> * 如果派生类的函数与基类的函数同名，但是参数不同。此时，不论有无virtual关键字，基类的函数将被**隐藏**
> * 如果派生类的函数与基类的函数同名，并且参数也相同，但是基类函数没有virtual关键字。此时，基类的函数被**隐藏**
```c++
#include <iostream>
using namespace std;

class A
{
public:
    void disp(){cout<<"A's disp"<<endl;}
    void test(){cout<<"class A"<<endl;}
private:
    int _a;
};

class B : public A
{
public:
    void test(){cout<<"class B"<<endl;} //B重写了A的成员函数test()
private:                                //从而隐藏了A的成员函数est()
    int _b;
};

int main()
{
    A a;
    B b;
    cout<<sizeof(a)<<endl;
    cout<<sizeof(b)<<endl;
    a.test();
    b.disp(); //B继承了A的成员函数disp()
    b.test(); 
}

```
输出
```
4
8
class A
A's disp
class B
```

* ### 覆盖 override
> 是指派生类函数覆盖基类函数，特征是：
（1）不同的范围（分别位于派生类与基类）；
（2）函数名字相同；
（3）参数相同；
（4）基类函数必须有virtual 关键字。
```c++
#include <iostream>
using namespace std;

class A
{
public:
	A() { _a = 0; }
    void disp(){cout<<"A's disp"<<endl;}
    virtual void test(){cout<<"class A"<<endl;}
private:
    int _a;
};

class B : public A
{
public:
    void test(){cout<<"class B"<<endl;}
private:
    int _b;
};

int main()
{
    A a;
    B b;
    cout<<sizeof(a)<<endl;
    cout<<sizeof(b)<<endl;
    a.test();
    b.disp();
    b.test();
}

```
输出
```
8
12
class A
A's disp
class B
```

`2019-07-10`
