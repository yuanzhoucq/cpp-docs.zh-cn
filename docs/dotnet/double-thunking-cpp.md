---
title: "双重 Thunk (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 双重形式转换"
  - "双重形式转换"
  - "互操作 [C++], 双重形式转换"
  - "互操作性 [C++], 双重形式转换"
  - "混合程序集 [C++], 双重形式转换"
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 双重 Thunk (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所谓双形式转换 \(Thunk\)，是指在托管上下文中的函数调用调用 Visual C\+\+ 托管函数以及程序执行为了调用托管函数而调用本机入口点时，您体验到的性能下降。  此主题讨论发生双形式转换 \(Thunk\) 发生的位置以及如何避免它以改进性能。  
  
## 备注  
 默认情况下，当使用 **\/clr**（而不是 **\/clr:pure**）进行编译时，托管函数的定义导致编译器生成一个托管入口点和一个本机入口点。  这允许从本机和托管调用站点调用托管函数。  但是，当存在本机入口点时，它可以是函数的所有调用的入口点。  如果调用函数是托管的，则本机入口点将调用托管入口点。  实际上，需要两个调用来调用该函数（因此，称为双形式转换 \(Thunk\)）。  例如，虚函数始终通过本机入口点调用。  
  
 一种解决方法是：通知编译器不要为托管函数生成本机入口点，这样只能通过使用 [\_\_clrcall](../cpp/clrcall.md) 调用约定从托管上下文调用此函数。  
  
 类似地，如果导出 \([dllexport、dllimport](../cpp/dllexport-dllimport.md)\) 托管函数，将生成本机入口点，并且导入和调用该函数的任何函数将通过本机入口点进行调用。  在这种情况下，若要避免双形式转换 \(Thunk\)，请不要使用本机导出\/导入语义；而应通过 `#using` 直接引用元数据（请参见 [\#using 指令](../preprocessor/hash-using-directive-cpp.md)）。  
  
 更新了编译器以减少不必要的双形式转换 \(Thunk\)。  例如，签名中具有托管类型（包括返回类型）的任何函数将隐式标记为 `__clrcall`。  有关双形式转换 \(Thunk\) 消除的更多信息，请 [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/01\/COptimizations\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx)参见。  
  
## 示例  
  
### 说明  
 下面的示例演示双形式转换 \(Thunk\)。  当编译本机（不使用 **\/clr**）时，对 `main` 中的虚函数的调用生成一个对 `T` 的复制构造函数的调用和一个对析构函数的调用。  当使用 **\/clr** 和 `__clrcall` 声明虚函数时会获得相似的行为。  然而，当仅使用 **\/clr** 编译时，该函数调用将生成对复制构造函数的调用，但是，由于本机到托管的形式转换 \(Thunk\)，并没有另一个对复制构造函数的调用。  
  
### 代码  
  
```  
// double_thunking.cpp  
// compile with: /clr  
#include <stdio.h>  
struct T {  
   T() {  
      puts(__FUNCSIG__);  
   }  
  
   T(const T&) {  
      puts(__FUNCSIG__);  
   }  
  
   ~T() {  
      puts(__FUNCSIG__);  
   }  
  
   T& operator=(const T&) {  
      puts(__FUNCSIG__);  
      return *this;  
   }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
  
   printf("calling struct S\n");  
   pS->f(t);  
   printf("after calling struct S\n");  
}  
```  
  
### 示例输出  
  
```  
__thiscall T::T(void)  
calling struct S  
__thiscall T::T(const struct T &)  
__thiscall T::T(const struct T &)  
__thiscall T::~T(void)  
__thiscall T::~T(void)  
after calling struct S  
__thiscall T::~T(void)  
```  
  
## 示例  
  
### 说明  
 前面的示例演示了存在双形式转换 \(Thunk\) 的情况。  本示例说明它的影响。  `for` 循环调用虚函数，并且程序报告执行时间。  当使用 **\/clr** 编译该程序时，会报告最慢的时间。  当不使用 **\/clr** 编译或者使用 `__clrcall` 声明虚函数时，会报告最快的时间。  
  
### 代码  
  
```  
// double_thunking_2.cpp  
// compile with: /clr  
#include <time.h>  
#include <stdio.h>   
  
#pragma unmanaged  
struct T {  
   T() {}  
   T(const T&) {}  
   ~T() {}  
   T& operator=(const T&) { return *this; }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
   clock_t start, finish;  
   double  duration;  
   start = clock();  
  
   for ( int i = 0 ; i < 1000000 ; i++ )  
      pS->f(t);  
  
   finish = clock();  
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);  
   printf( "%2.1f seconds\n", duration );  
   printf("after calling struct S\n");  
}  
```  
  
### 示例输出  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)