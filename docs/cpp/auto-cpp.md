---
title: "自动 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 334006e8ad06bdc174922d57d97d2d0f0335cf34
ms.sourcegitcommit: 4e01d36ffa64ea11bacf589f79d2f1df947e2510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2018
---
# <a name="auto-c"></a>自动 （c + +）
从其初始化表达式中推导声明的变量的类型。  
  
## <a name="syntax"></a>语法  
  
```  
auto declarator initializer;  
```  
  
```  
[](auto param1, auto param2) {};  
```  
  
## <a name="remarks"></a>备注  
 `auto` 关键字指示编译器使用已声明变量的初始化表达式或 lambda 表达式参数来推导其类型。  
  
 在大多情况下，建议您使用 `auto` 关键字（除非您确实需要转换），因为此关键字可提供以下好处：  
  
-   **可靠性：**如果表达式的类型会更改 — 包括函数返回类型发生更改 — 它也能工作。  
  
-   **性能：**确保不将任何转换。  
  
-   **可用性：**你不必担心类型名称拼写困难和拼写有误。  
  
-   **效率：**代码可能会更有效。  
  
 可能不需要使用 `auto` 的转换情况：  
  
-   当需要特定类型且不需要执行任何其他操作时。  
  
-   表达式模板帮助程序类型-例如， `(valarray+valarray)`。  
  
 若要使用 `auto` 关键字，请使用此关键字代替一种类型来声明变量，并指定初始化表达式。 此外，还可通过使用说明符和声明符（如 `auto`、`const`）、指针 (`volatile`)、引用 (`*`) 以及右值引用 (`&`) 来修改 `(&&` 关键字。 编译器计算初始化表达式，然后使用该信息来推断变量类型。  
  
 初始化表达式可以是赋值 （等号语法），直接初始化 （函数样式语法）、[运算符 new](new-operator-cpp.md)表达式或初始化表达式可以是*有关范围声明*中的参数[基于范围的语句 （c + +）](../cpp/range-based-for-statement-cpp.md)语句。 有关详细信息，请参阅[初始值设定项](../cpp/initializers.md)和在本文档后面的代码示例。  
  
 `auto` 关键字是类型的占位符，但它本身不是类型。 因此，`auto`关键字不能在强制转换或运算符如[sizeof](../cpp/sizeof-operator.md)和[typeid](../windows/typeid-cpp-component-extensions.md)。  
  
## <a name="usefulness"></a>有用性  
 `auto` 关键字是声明复杂类型变量的简单方法。 例如，可使用 `auto` 声明一个变量，其中初始化表达式涉及模板、指向函数的指针或指向成员的指针。  
  
 也可使用 `auto` 声明变量并将其初始化为 lambda 表达式。 您不能自行声明变量的类型，因为仅编译器知道 lambda 表达式的类型。 有关详细信息，请参阅[Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)。  
  
## <a name="trailing-return-types"></a>尾部的返回类型  
 您可将 `auto` 与 `decltype` 类型说明符一起使用来帮助编写模板库。 使用 `auto` 和 `decltype` 声明其返回类型取决于其模板参数类型的模板函数。 或者，使用 `auto` 和 `decltype` 声明包装对其他函数的调用，然后返回该函数的任一返回类型的模板函数。 有关详细信息，请参阅[decltype](../cpp/decltype-cpp.md)。  
  
## <a name="references-and-cv-qualifiers"></a>引用和 cv 限定符  
 请注意，使用 `auto` 会删除引用、const 限定符和 volatile 限定符。 请看下面的示例：  
  
```cpp  
// cl.exe /analyze /EHsc /W4  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
    int count = 10;  
    int& countRef = count;  
    auto myAuto = countRef;  
  
    countRef = 11;  
    cout << count << " ";  
  
    myAuto = 12;  
    cout << count << endl;  
}  
  
```  
  
 在前面的示例中，myAuto 是一个 int，而不是一个 int 引用，，因此输出`11 11`，而不`11 12`会出现这种情况，如果尚未删除引用限定符`auto`。  
  
## <a name="type-deduction-with-braced-initializers-c14"></a>具有大括号内的初始值设定项 (C + + 14) 的类型推导  
 下面的代码 exmample 演示如何初始化使用大括号的自动变量。 请注意之间 A 和 B 和 C 之间的差异和 e。  
  
```cpp  
#include <initializer_list>  
  
int main()  
{  
    // std::initializer_list<int>  
    auto A = { 1, 2 };  
  
    // std::initializer_list<int>  
    auto B = { 3 };  
  
    // int  
    auto C{ 4 };  
  
    // C3535: cannot deduce type for 'auto' from initializer list'  
    auto D = { 5, 6.7 };  
  
    // C3518 in a direct-list-initialization context the type for 'auto'  
    // can only be deduced from a single initializer expression  
    auto E{ 8, 9 };  
  
    return 0;  
}  
```  
  
## <a name="restrictions-and-error-messages"></a>限制和错误消息  
 下表列出了使用 `auto` 关键字的限制，及编译器发出的相应诊断错误消息。  
  
|错误号|描述|  
|------------------|-----------------|  
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|`auto` 关键字不能与任何其他类型说明符组合。|  
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|使用 `auto` 关键字声明的符号必须具有初始值设定项。|  
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|你错误地使用了 `auto` 关键字来声明类型。 例如，声明了方法返回类型或数组。|  
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|不能使用 `auto` 关键字声明参数或模板参数。|  
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|不能使用 `auto` 关键字声明的方法或模板参数。|  
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|符号初始化之前无法使用。 在实践中，这意味着无法使用变量来初始化自身。|  
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|无法强制转换为使用 `auto` 关键字声明的类型。|  
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|使用 `auto` 关键字声明的声明符列表中的所有符号必须解析为相同的类型。 有关详细信息，请参阅[声明和定义](declarations-and-definitions-cpp.md)。|  
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|[Sizeof](../cpp/sizeof-operator.md)和[typeid](../windows/typeid-cpp-component-extensions.md)运算符不能应用于使用声明的符号`auto`关键字。|  
  
## <a name="examples"></a>示例  
 这些代码片段阐释了可使用 `auto` 关键字的一些方法。  
  
 下面的声明等效。 在第一个语句中，将变量 `j` 声明为类型 `int`。 在第二个语句中，将变量 `k` 推导为类型 `int`，因为初始化表达式 (0) 是整数。  
  
```cpp  
int j = 0;  // Variable j is explicitly type int.  
auto k = 0; // Variable k is implicitly type int because 0 is an integer.  
```  
  
 以下声明等效，但第二个声明比第一个更简单。 使用 `auto` 关键字的最令人信服的一个原因是简单。  
  
```cpp  
map<int,list<string>>::iterator i = m.begin();   
auto i = m.begin();   
```  
  
 当 `iter` 和范围 `elem` 循环启动时，下列代码片段将声明变量 `for` 和 `for` 的类型。  
  
```cpp  
// cl /EHsc /nologo /W4  
#include <deque>  
using namespace std;  
  
int main()  
{  
    deque<double> dqDoubleData(10, 0.1);  
  
    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)  
    { /* ... */ }  
  
    // prefer range-for loops with the following information in mind  
    // (this applies to any range-for with auto, not just deque)  
  
    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples  
    { /* ... */ }  
  
    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE  
    { /* ... */ }  
  
    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE  
    { /* ... */ }  
}  
```  
  
 下面的代码片段使用 `new` 运算符和指针声明来声明指针。  
  
```cpp  
double x = 12.34;  
auto *y = new auto(x), **z = new auto(&x);  
```  
  
 下一个代码片段在每个声明语句中声明多个符号。 请注意，每个语句中的所有符号将解析为同一类型。  
  
```cpp  
auto x = 1, *y = &x, **z = &y; // Resolves to int.  
auto a(2.01), *b (&a);         // Resolves to double.  
auto c = 'a', *d(&c);          // Resolves to char.  
auto m = 1, &n = m;            // Resolves to int.  
```  
  
 此代码片段使用条件运算符 (`?:`) 将变量 `x` 声明为值为 200 的整数：  
  
```cpp  
int v1 = 100, v2 = 200;  
auto x = v1 > v2 ? v1 : v2;  
```  
  
 下面的代码段初始化变量`x`类型`int`、 可变`y`到类型的引用`const int`，和变量`fp`为指向返回类型的函数的`int`。  
  
```cpp  
int f(int x) { return x; }  
int main()  
{  
    auto x = f(0);  
    const auto & y = f(1);  
    int (*p)(int x);  
    p = f;  
    auto fp = p;  
    //...  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../cpp/auto-keyword.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [/Zc: auto （推导变量类型）](../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 运算符](../cpp/sizeof-operator.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)   
 [new 运算符](new-operator-cpp.md)   
 [声明和定义](declarations-and-definitions-cpp.md)   
 [Lambda 表达式的示例](../cpp/examples-of-lambda-expressions.md)   
 [初始值设定项](../cpp/initializers.md)   
 [decltype](../cpp/decltype-cpp.md)