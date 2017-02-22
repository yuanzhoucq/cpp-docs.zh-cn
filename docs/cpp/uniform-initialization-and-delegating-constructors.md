---
title: "统一安装和委派构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# 统一安装和委派构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在现代C\+\+中，你可以使用 *括号初始化* 为任意类型，不带等号。  此外，执行类似的工作的多个构造函数时，还可以使用委托的构造函数简化代码。  
  
## 大括号初始化  
 可以为所有选件类、结构或联合使用大括号初始化。  如果类型默认构造函数值，隐式或显式声明，可以使用默认值初始化大括号 \(具有空大括号\)。  例如，通过使用默认值和非默认的大括号初始化，下面的选件类可以初始化：  
  
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
  
 如果一个类具有非默认构造函数，其中类成员出现在大括号初始化的顺序是对应的参数出现在构造函数中，而不是为了在其中的成员被声明（如在前面的例子 `class_a` ）。  否则，如果该类型没有声明构造函数，成员将显示在大括号初始值设定项的排序不相同。声明它们的排序；在这种情况下，可以按你所希望的初始化许多公共成员，但是，不能跳过任何成员。  下面的示例演示，当没有声明的构造函数时，用于大括号初始化的排序：  
  
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
  
 如果默认值构造函数显式声明，但被标记为已删除，默认值不能使用大括号初始化：  
  
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
  
 您可以使用大括号初始化任何地方，在你做初始化处，例如，作为函数参数或返回值，或用 `new` 关键字：  
  
```cpp  
class_d* cf = new class_d{4.5};  
kr->add_d({ 4.5 });  
return { 4.5 };  
  
```  
  
## initializer\_list 构造函数  
 该 [initializer\_list Class](../standard-library/initializer-list-class.md) 表示可以在构造函数中使用指定类型的对象的列表和其他情况下。  使用大括号初始化，可构造 initializer\_list:  
  
```cpp  
initializer_list<int> int_list{5, 6, 7};  
```  
  
> [!IMPORTANT]
>  为了使用这个类，必须引用 [\<initializer\_list\>](../standard-library/initializer-list.md) 头文件。  
  
 `initializer_list` 可以被复制。  在这种情况下，成员的新列表是对原始项的成员的引用列表：  
  
```cpp  
initializer_list<int> ilist1{ 5, 6, 7 };  
initializer_list<int> ilist2( ilist1 );  
if (ilist1.begin() == ilist2.begin())  
    cout << "yes" << endl; // expect "yes"  
  
```  
  
 标准库容器类， `string`, `wstring`, 和 `regex` 也有 `initializer_list` 容器。  下面的示例演示如何对这些构造函数的大括号初始化：  
  
```cpp  
vector<int> v1{ 9, 10, 11 };   
map<int, string> m1{ {1, "a"}, {2, "b"} };  
string s{ 'a', 'b', 'c' };   
regex rgx{'x', 'y', 'z'};   
```  
  
## 委托构造函数  
 许多选件类具有执行类似内容 \(例如的多个构造函数，验证参数：  
  
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
  
 你可以通过添加一个函数，完成所有的验证减少重复的代码，但是对于 `class_c` 如果一个构造函数可以委托一些工作到另一个，会更容易理解和维护。  要添加委托构造函数，使用 `constructor (. . .) : constructor (. . .)` 语法：  
  
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
  
 当你通过前面的例子步骤，注意构造 `class_c(int, int, int)` 首先调用构造函数 `class_c(int, int)`，其中反过来调用 `class_c(int)`。  每个构造函数执行不受其他构造函数仅执行的工作。  
  
 调用第一个构造函数初始化对象，以使其所有成员在那点初始化。  您不能对委托给另一个构造函数的成员初始化，如下所示：  
  
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
  
 下一个示例演示使用非静态数据成员初始值设定项。  请注意，如果构造函数还初始化特定的数据成员，成员初始值设定项中重写：  
  
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
  
 委托构造函数语法不会阻止递归 Constructor1 调用 Constructor2 调用 Constructor1 和错误不会引发构造函数的意外创建，直到有堆栈溢出。  您应当避免循环。  
  
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