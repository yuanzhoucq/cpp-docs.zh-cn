---
title: "编译器错误 C2059 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2059
dev_langs:
- C++
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: dbf80ab803eaaacc29ac82657af130194417f1c7
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2059"></a>编译器错误 C2059
语法错误: token  
  
 该标记导致语法错误。  
  
 下面的示例生成声明的行的错误消息`j`。  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 若要确定错误的原因，请检查错误消息中列出的行不仅上面的行。 如果对行的检查任何线索有关的问题，请尝试注释掉错误消息中列出的一行，并可能对上面的若干行。  
  
 如果在紧随的符号上会出现该错误消息`typedef`变量，请确保该变量已定义的源代码中。  
  
 如果符号计算结果为执行任何操作，可能会发生，可能会 C2059 时**/D** `symbol`  **=** 用于编译。  
  
```  
// C2059a.cpp  
// compile with: /DTEST=  
#include <stdio.h>  
  
int main() {  
   #ifdef TEST  
      printf_s("\nTEST defined %d", TEST);   // C2059  
   #else  
      printf_s("\nTEST not defined");  
   #endif  
}  
```  
  
 在其中会发生 C2059 的另一种是在编译的应用程序中的函数的默认自变量指定了结构时。 自变量的默认值必须是一个表达式。 初始值设定项列表-例如，一个用于初始化结构 — 不是表达式。  若要解决此问题，请定义一个构造函数来执行所需的初始化。  
  
 下面的示例生成 C2059:  
  
```  
// C2059b.cpp  
// compile with: /c  
struct ag_type {  
   int a;  
   float b;  
   // Uncomment the following line to resolve.  
   // ag_type(int aa, float bb) : a(aa), b(bb) {}   
};  
  
void func(ag_type arg = {5, 7.0});   // C2059  
void func(ag_type arg = ag_type(5, 7.0));   // OK  
```  
  
 如果你定义的成员模板类或函数的类之外，还可以获取 C2059。 有关信息，请参阅[知识库文章 241949](http://support.microsoft.com/kb/241949)。  
  
 C2059 可能格式不正确的强制转换。  
  
 下面的示例生成 C2059:  
  
```  
// C2059c.cpp  
// compile with: /clr  
using namespace System;  
ref class From {};  
ref class To : public From {};  
  
int main() {  
   From^ refbase = gcnew To();  
   To^ refTo = safe_cast<To^>(From^);   // C2059  
   To^ refTo2 = safe_cast<To^>(refbase);   // OK  
}  
```  
  
 如果你尝试创建命名空间名称包含句点，也会发生 C2059。  
  
 下面的示例生成 C2059:  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 时可限定名称的运算符会发生 C2059 (`::`， `->`，和`.`) 关键字后面必须跟`template`，此示例中所示：  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::Rebind<X>::Other AX; // error C2059  
};  
  
```  
  
 默认情况下，C++ 会假定 `AY::Rebind` 不是模板；因此，后面的 `<` 解释为小于号。  必须显式告知编译器 `Rebind` 是模板，以便其正确分析尖括号。 若要更正此错误，请在依赖类型的名称上使用 `template` 关键字，如下所示：  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::template Rebind<X>::Other AX; // correct  
};  
  
```
