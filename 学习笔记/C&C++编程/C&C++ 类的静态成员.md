## 静态成员变量
* 关键字`static`修饰
* 属于类与不属于某个对象，意思是说这个成员对象将被创建于静态存储区，为全局变量
* 在类中声明之后，必须在**类外进行初始化（定义）**
## 静态成原函数
* 起初并没有静态成员函数，只有静态成员变量
* 静态成员函数只访问静态成员变量

```
#include <iostream>
using namespace std;

class A
{
public:
	void Set_a1(int a1) { _a1 = a1; }
	void Set_a2(int a2) { _a2 = a2; }
	void Disp(void) { cout << _a1 << "," << _a2 << endl; }
private:
	static int _a1;
	int _a2;
};

int A::_a1 = 0; 

int main()
{
	A a;
	a.Set_a2(0);
	a.Disp();
	cout << sizeof(a) << endl;
	a.Set_a1(1000);
	a.Set_a2(2000);
	a.Disp();
}

```
输出：
```
0,0
4
1000,2000
```
