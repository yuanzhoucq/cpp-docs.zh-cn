---
title: "if-else 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 7f6d2a553e34b5f15e53fa142241af83d8e91255
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="if-else-statement-c"></a>if-else 语句 (C++)
控件条件分支。 中的语句*if 块*只有当执行*if 表达式*计算结果为非零值 (或`true`)。 如果值*表达式*不为零， *statement1*执行块中的任何其他语句和而 else-块中，如果存在，则跳过。 如果值*表达式*是零，则如果块已跳过，并且其他的如果存在，将执行此块。 表达式计算结果为非零值。
- `true`
- 非 null 指针，
- 任何非零算术值，或 
- 类定义明确转换为算术、 布尔值或指针类型。 (有关转换的信息，请参阅[标准转换](../cpp/standard-conversions.md)。)   
  
## <a name="syntax"></a>语法  
  
```  
  
if ( expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
} 

// Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )  
{
   statement1;
   ...  
}
else  // optional
{
   statement2;
   ...
}  

// Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
} 
```  
## <a name="example"></a>示例  
```  
// if_else_statement.cpp  
#include <iostream>

using namespace std;

class C
{
    public:
    void do_somthing(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

  // no else statement
    if (x == 10)
    {
        x = 0; 
    }
    
  
    C* c;
  init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```  
## <a name="if-statement-with-an-initializer"></a>如果使用初始值设定项的语句
**Visual Studio 2017 15.3 及更高版本**(适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):**如果**语句还可能包含声明和初始化命名的变量的表达式。 如果块的作用域内仅需要变量时，请使用这种形式的 if 语句。 

```cpp
## Example  
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>


using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }


    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }

}
```

 中的所有窗体**如果**语句，*表达式*，它可以具有一个结构以外的任何值将计算，包括所有副作用。 控制权将传递从**如果**语句到程序中下一步语句除非之一*语句*s 包含[中断](../cpp/break-statement-cpp.md)，[继续](../cpp/continue-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md)。  
  
 **其他**子句`if...else`语句是与最近关联以前**如果**中没有相应的相同作用域语句**其他**语句。   

## <a name="constexpr-if-statements"></a>constexpr 如果语句
**Visual Studio 2017 15.3 及更高版本**(适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 在函数模板，你可以使用**constexpr 如果**语句使编译时分支决策而无需采用多个函数重载。 例如，你可以编写单个函数该句柄参数解包 （零参数重载均不需要）： 

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
// handle t
   do_something(t);

   // handle r conditionally
   constexpr if (sizeof...(r)) 
   {
      
      f(r...); 
   }
   else
   {
       g(r...);
   }
}
```

  
 
## <a name="see-also"></a>另请参阅  
 [选择语句](../cpp/selection-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [switch 语句 (C++)](../cpp/switch-statement-cpp.md)
