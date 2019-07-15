## C中的字符串
* 字符数组组成字符串，通过指针访问字符串
* 字符串常量如`"123456789"`，编译器会自动在后面加入字符`\0`，作为字符串输出结束的标志
```C++
#include <iostream>
using namespace std;

void print_onebyone(char const* str,int length)
{
	for (int i = 0; i < length; i++)
	{
		cout << i << "th of string is ";
		if (*(str + i) == '\0')
		{
			cout << "NULL" << endl;
		}
		else
		{
			cout << *(str + i) << endl;
		}
	}
}

int main(void)
{
	char str1[] = "123456789";
	char str2[20] = "123456789"; //其余初始化为'\0'

	cout << sizeof(str1) << endl;
	cout << sizeof(str2) << endl;

	print_onebyone(str1, sizeof(str1));
	print_onebyone(str2, sizeof(str2));
}
```
### C字符串操作函数
* `string.h`
* `strcpy`，`strlen'，`strcat`等

## C++字符串
* 引入string类

