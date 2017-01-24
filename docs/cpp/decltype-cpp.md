---
title: "decltype (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "decltype"
  - "decltype_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "decltype 运算符"
  - "运算符 [C++], decltype"
  - "运算符 [C++], 推导表达式类型"
  - "运算符 [C++], 表达式的类型"
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# decltype (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`decltype` 类型说明符生成指定表达式的类型。  `decltype` 类型说明符与 [auto 关键字](../cpp/auto-cpp.md)一起主要对编写模板库的开发人员有用。  使用 `auto` 和 `decltype` 声明其返回类型取决于其模板参数类型的模板函数。  或者，使用 `auto` 和 `decltype` 声明包装对其他函数的调用，然后返回包装函数的返回类型的模板函数。  
  
## 语法  
  
```  
decltype( expression )  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`expression`|一个表达式。  有关详细信息，请参阅[表达式](../cpp/expressions-cpp.md)。|  
  
## 返回值  
 `expression` 参数的类型。  
  
## 备注  
 `decltype` 类型说明符在 Visual C\+\+ 2010 或更高版本中受支持，并可与本机或托管代码一起使用。  Visual Studio 2015 及更高版本支持 `decltype(auto)` \(C\+\+14\)。  
  
 编译器使用下列规则来确定 `expression` 参数的类型。  
  
-   如果 `expression` 参数是标识符或[类成员访问](../cpp/member-access-operators-dot-and.md)，则 `decltype(``expression``)` 是 `expression` 命名的实体的类型。  如果不存在此类实体或 `expression` 参数命名一组重载函数，则编译器将生成错误消息。  
  
-   如果 `expression` 参数是对一个函数或一个重载运算符函数的调用，则 `decltype(``expression``)` 是函数的返回类型。  将忽略重载运算符两边的括号。  
  
-   如果 `expression` 参数是[右值](../cpp/lvalues-and-rvalues-visual-cpp.md)，则 `decltype(``expression``)` 是 `expression` 类型。  如果 `expression` 参数是[左值](../cpp/lvalues-and-rvalues-visual-cpp.md)，则 `decltype(``expression``)` 是对 [左值引用](../cpp/lvalue-reference-declarator-amp.md) 类型的`expression`。  
  
 下面的代码示例演示 `decltype` 类型标识符的一些用途。  首先，假定已编码下列语句。  
  
```  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 接下来，请检查由下表中四个 `decltype` 语句返回的类型。  
  
|语句|类型|注释|  
|--------|--------|--------|  
|`decltype(fx());`|`const int&&`|对 [左值引用](../cpp/rvalue-reference-declarator-amp-amp.md) 的`const int`。|  
|`decltype(var);`|`int`|变量 `var` 的类型。|  
|`decltype(a->x);`|`double`|成员访问的类型。|  
|`decltype((a->x));`|`const double&`|内部括号导致语句作为表达式而不是成员访问计算。  由于 `a` 声明为 `const` 指针，因此类型是对 `const double` 的引用。|  
  
## Decltype 和 Auto  
 在 C\+\+14 中，可以使用不带尾随返回类型的  `decltype(auto)` 来声明其返回类型取决于其模板参数类型的模板函数。  
  
 在 C\+\+11 中，可以结合使用尾随返回类型上的 `decltype` 类型说明符和 `auto` 关键字来声明其返回类型依赖于其模板参数类型的模板函数。  例如，考虑下面的代码示例，其中模板函数的返回类型取决于模板参数类型。  在代码示例中，*未知*占位符指示无法指定返回类型。  
  
```  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 `decltype` 类型说明符的引入使开发人员能够获取模板函数返回的表达式的类型。  请使用稍后演示的替代函数声明语法、`auto` 关键字和 `decltype` 类型说明符来声明后指定返回类型。  后指定返回类型是在对声明进行编译而不是编码时确定的。  
  
 以下原型阐述一个替代函数声明的语法。  请注意，`const` 和 `volatile` 限定符以及 `throw` [异常规范](../cpp/exception-specifications-throw-cpp.md)都是可选的。  *function\_body* 占位符表示指定函数作用的复合语句。  作为最佳编码做法，`decltype` 语句中的*表达式*占位符应与 *function\_body* 中 `return` 语句（如果有）指定的表达式匹配。  
  
 `auto` *function\_name*`(`*参数*opt`)` `const`opt `volatile`opt `−>` `decltype(`*表达式*`)` `throw`opt `{`*function\_body*`};`  
  
 在下面的代码示例中，`myFunc` 模板函数的后指定返回类型取决于 `t` 和 `u` 模板参数的类型。  作为最佳编码做法，此代码示例还使用右值引用和 `forward` 函数模板来支持完美转发。  有关详细信息，请参阅 [规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
```  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## Decltype 和转发函数 \(C\+\+11\)  
 转发函数包装对其他函数的调用。  请考虑将其参数或包含这些参数的表达式的结果转发到其他函数的函数模板。  此外，转发函数返回调用其他函数的结果。  在此方案中，转发函数的返回类型应与包装函数的返回类型相同。  
  
 在此方案中，没有 `decltype` 类型说明符，您无法编写适当的类型表达式。  `decltype` 类型说明符将启用泛型转发函数，因为该说明符不会丢失有关函数是否返回引用类型的必需信息。  有关转发函数的代码示例，请参阅上面的 `myFunc` 模板函数示例。  
  
## 示例  
 下面的代码示例声明模板函数 `Plus()` 的后指定返回类型。  `Plus` 函数将使用 `operator+` 重载处理其两个操作数。  因此，对 `Plus` 函数的加运算符 \(\+\) 和返回类型的解释取决于函数参数的类型。  
  
```  
// decltype_1.cpp  
// compile with: /EHsc  
//  
#include "stdafx.h"  
#include <iostream>  
#include <string>  
#include <utility>  
#include <iomanip>  
  
using namespace std;  
  
template<typename T1, typename T2>  
auto Plus(T1&& t1, T2&& t2) ->   
   decltype(forward<T1>(t1) + forward<T2>(t2))  
{  
   return forward<T1>(t1) + forward<T2>(t2);  
}  
  
class X  
{  
   friend X operator+(const X& x1, const X& x2)  
   {  
      return X(x1.m_data + x2.m_data);  
   }  
  
public:  
   X(int data) : m_data(data) {}  
   int Dump() const { return m_data;}  
private:  
   int m_data;  
};  
  
int main()  
{  
   // Integer   
   int i = 4;  
   cout <<   
      "Plus(i, 9) = " <<   
      Plus(i, 9) << endl;  
  
   // Floating point  
   float dx = 4.0;  
   float dy = 9.5;  
   cout <<     
      setprecision(3) <<   
      "Plus(dx, dy) = " <<  
      Plus(dx, dy) << endl;  
  
   // String        
   string hello = "Hello, ";  
   string world = "world!";  
   cout << Plus(hello, world) << endl;  
  
   // Custom type  
   X x1(20);  
   X x2(22);  
   X x3 = Plus(x1, x2);  
   cout <<   
      "x3.Dump() = " <<   
      x3.Dump() << endl;  
}  
```  
  
 **输出**  
  
 此代码示例将生成下列结果。  
  
 13  
  
 13.5  
  
 Hello, world\!  
  
 42  
  
## 要求  
 Visual C\+\+ 2010 或更高版本。  
  
 decltype\(auto\) 要求 Visual Studio 2015 或更高版本  
  
## 请参阅  
 [简单类型名称](http://msdn.microsoft.com/zh-cn/333f45cb-2c72-4d81-8e59-e346b05f55e3)