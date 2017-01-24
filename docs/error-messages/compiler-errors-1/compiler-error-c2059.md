---
title: "编译器错误 C2059 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2059"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2059"
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2059
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 :“token”  
  
 该标记导致语法错误。  
  
 下面的示例对声明 `j` 的行生成了错误消息。  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 若要确定该错误的原因，则不仅要检查在错误消息中列出的行，还要检查该行上面的行。  如果对行的检查没有获得有关可能出现的问题的任何线索，则尝试注释掉在错误消息中列出的行以及可能出现在该行上面的若干行。  
  
 如果该错误消息在紧跟 `typedef` 变量的符号上出现，则确保该变量是否已在源代码中定义。  
  
 如果符号没有计算出任何结果（在使用 **\/D**`symbol`**\=** 编译时可能发生），可能会导致 C2059。  
  
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
  
 可能收到 C2059 的另一个特定原因是编译在函数的默认参数中指定了结构的应用程序。  参数的默认值必须是一个表达式。  初始值设定项列表—如，用于初始化结构的初始值设定项列表—不是表达式。若要解决该问题，定义一个执行所需初始化的构造函数。  
  
 下面的示例生成 C2059：  
  
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
  
 如果您在类外定义成员模板类或函数，也可能获得 C2059。  有关更多信息，请参见 [知识库文章 241949](http://support.microsoft.com/kb/241949)。  
  
 对于格式错误的强制转换，会发生 C2059。  
  
 下面的示例生成 C2059：  
  
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
  
 如果尝试创建一个包含句点的命名空间名称，也会发生 C2059。  
  
 下面的示例生成 C2059：  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 C2059可发生，当一个可以限定名称的运算符 \(`::`、`->`和 `.`\) 必须后跟 `template`关键字时，如该例中所示：  
  
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
  
 默认情况下，C\+\+假设 `AY::Rebind` 不是模板；因此，下面的 `<` 解释为小于号。必须显式告诉编译器 `Rebind` 是通过模板，以便可以正确分析尖括号。  若要更正此错误，请使用上依赖类型名称的 `template` 关键字，如下所示：  
  
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