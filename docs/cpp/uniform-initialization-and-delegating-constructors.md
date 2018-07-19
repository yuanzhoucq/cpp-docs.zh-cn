---
title: 统一初始化和委派构造函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92174ceefa350b739567ac3e67c2ca023afb6008
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939827"
---
# <a name="uniform-initialization-and-delegating-constructors"></a>初始化和委派构造函数
在现代 C++ 中，你可以使用*大括号初始化*对于任何类型，而无需等号。 此外，当你具有执行类似工作的多个构造函数时，你可使用委托构造函数简化代码。  
  
## <a name="brace-initialization"></a>大括号初始化  
 您可以为任何类、结构或联合使用大括号初始化。 如果类型具有隐式或显式声明的默认构造函数，则您可以使用默认大括号初始化（具有空大括号）。 例如，可通过使用默认和非默认大括号初始化来初始化以下类：  
  
```cpp  
#include <string>  
using namespace std;  
  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}  
double m_double;  
string m_string;  
};  
  
int main()  
{  
    class_a c1{};  
    class_a c1_1;  
  
    class_a c2{ "ww" };  
    class_a c2_1("xx");  
  
    // order of parameters is the same as the constructor  
    class_a c3{ "yy", 4.4 };  
    class_a c3_1("zz", 5.5);  
}  
  
```  
  
 如果类具有非默认构造函数，则类成员在大括号初始值设定项中的显示顺序是对应参数在构造函数中的显示顺序，而不是成员的声明顺序（如上一示例中的 `class_a` 一样）。 否则，如果类型没有声明的构造函数，则成员在大括号初始值设定项中的显示顺序与其声明顺序一样，在这种情况下，您可初始化所需数量的公共成员，但无法跳过任何成员。 以下示例演示了在无声明的构造函数时在大括号初始化中使用的顺序：  
  
```cpp  
class class_d {  
public:  
    float m_float;  
    string m_string;  
    wchar_t m_char;  
};  
  
int main()  
{  
    class_d d1{};  
    class_d d1{ 4.5 };  
    class_d d2{ 4.5, "string" };  
    class_d d3{ 4.5, "string", 'c' };  
  
    class_d d4{ "string", 'c' }; // compiler error  
    class_d d5("string", 'c', 2.0 }; // compiler error  
}   
```  
  
 如果默认构造函数已显式声明，但标记为“已删除”，则无法使用默认大括号初始化：  
  
```cpp  
class class_f {  
public:  
    class_f() = delete;  
    class_f(string x): m_string { x } {}  
    string m_string;  
};  
int main()  
{  
    class_f cf{ "hello" };  
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function  
}  
```  
  
 可以使用大括号初始化任意位置通常会执行初始化-例如，作为函数参数或返回值，或使用**新**关键字：  
  
```cpp  
class_d* cf = new class_d{4.5};  
kr->add_d({ 4.5 });  
return { 4.5 };  
  
```  
  
## <a name="initializerlist-constructors"></a>initializer_list 构造函数  
 [Initializer_list 类](../standard-library/initializer-list-class.md)表示只能在构造函数，并且在其他上下文中的指定类型的对象的列表。 您可通过使用大括号初始化构造 initializer_list：  
  
```cpp  
initializer_list<int> int_list{5, 6, 7};  
```  
  
> [!IMPORTANT]
>  若要使用此类，必须包括[< initializer_list >](../standard-library/initializer-list.md)标头。  
  
 可以复制 `initializer_list`。 在这种情况下，新列表的成员是对原始列表成员的引用：  
  
```cpp  
initializer_list<int> ilist1{ 5, 6, 7 };  
initializer_list<int> ilist2( ilist1 );  
if (ilist1.begin() == ilist2.begin())  
    cout << "yes" << endl; // expect "yes"  
  
```  
  
 标准库容器类以及 `string`、`wstring` 和 `regex` 具有 `initializer_list` 构造函数。 以下示例演示如何使用这些构造函数执行大括号初始化：  
  
```cpp  
vector<int> v1{ 9, 10, 11 };   
map<int, string> m1{ {1, "a"}, {2, "b"} };  
string s{ 'a', 'b', 'c' };   
regex rgx{'x', 'y', 'z'};   
```  
  
## <a name="delegating-constructors"></a>委派构造函数  
 许多类具有执行类似操作（例如参数验证）的多个构造函数  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c() {}  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) {   
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) {  
        max = my_max > 0 ? my_max : 10;  
        min = my_min > 0 && my_min < max ? my_min : 1;  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
    }  
};  
```  
  
 您可以通过添加一个执行所有验证的函数来减少重复的代码，但是如果一个构造函数可以将部分工作委托给其他构造函数，则 `class_c` 的代码更易于了解和维护。 若要添加委托构造函数，请使用 `constructor (. . .) : constructor (. . .)` 语法：  
  
```cpp  
class class_c {  
public:  
    int max;  
    int min;  
    int middle;  
  
    class_c(int my_max) {   
        max = my_max > 0 ? my_max : 10;   
    }  
    class_c(int my_max, int my_min) : class_c(my_max) {   
        min = my_min > 0 && my_min < max ? my_min : 1;  
    }  
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){  
        middle = my_middle < max && my_middle > min ? my_middle : 5;  
}  
};  
int main() {  
  
    class_c c1{ 1, 3, 2 };  
}  
  
```  
  
 当您单步调试上一示例时，请注意，构造函数 `class_c(int, int, int)` 首先调用构造函数 `class_c(int, int)`，该构造函数反过来调用 `class_c(int)`。 每个构造函数将仅执行其他构造函数不会执行的工作。  
  
 调用的第一个构造函数将初始化对象，以便此时初始化其所有成员。 您不能在委托给其他构造函数的构造函数中执行成员初始化，如下所示：  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    // member initialization here, no delegate  
    class_a(string str) : m_string{ str } {}  
  
    //can’t do member initialization here  
    // error C3511: a call to a delegating constructor shall be the only member-initializer  
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}  
  
    // only member assignment  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string;  
};  
  
```  
  
 下一示例演示非静态数据成员初始值设定项的使用。 请注意，如果构造函数还将初始化给定数据成员，则将重写成员初始值设定项：  
  
```cpp  
class class_a {  
public:  
    class_a() {}  
    class_a(string str) : m_string{ str } {}  
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }  
    double m_double{ 1.0 };  
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };  
};  
  
int main() {  
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"  
    int y = 4;  
}  
```  
  
 构造函数委托语法不会阻止意外创建构造函数递归 - Constructor1 将调用 Constructor2（其调用 Constructor1），在出现堆栈溢出之前不会出错。 您应当避免循环。  
  
```cpp  
class class_f{  
public:  
    int max;  
    int min;  
  
    // don't do this  
    class_f() : class_f(6, 3){ }  
    class_f(int my_max, int my_min) : class_f() { }  
};  
```