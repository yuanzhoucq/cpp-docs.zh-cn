---
title: 双重形式转换 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 47d5bbbecc8e1b9743c543a503df1a0afa0dc0ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="double-thunking-c"></a>双重 Thunk (C++)
双重形式转换是指的是托管的上下文调用 Visual c + + 托管函数，并且其中程序执行函数调用以便调用托管的函数调用函数的本机入口点时，你可以遇到的性能下降。 本主题讨论双重形式转换发生的位置以及如何避免来提高性能。  
  
## <a name="remarks"></a>备注  
 默认情况下，使用编译时 **/clr**，托管函数的定义使编译器生成一个托管的入口点和一个本机入口点。 这允许从本机和托管调用站点调用托管的函数。 但是，如果存在一个本机入口点，它可以是对函数的所有调用的入口点。 如果托管的调用函数，本机入口点则将调用的托管的入口点。 实际上，需要两个调用来调用该函数 （因此，双形式转换）。 例如，通过一个本机入口点始终调用虚函数。  
  
 一个解决方法是以告知编译器不生成托管函数，一个本机入口点，该函数将仅调用从非托管上下文中，通过使用[__clrcall](../cpp/clrcall.md)调用约定。  
  
 同样，如果导出 ([dllexport、 dllimport](../cpp/dllexport-dllimport.md)) 托管的函数，生成一个本机入口点，并且任何函数，用于导入并调用该函数将调用通过本机入口点。 若要避免双重形式转换在此情况下，不要使用本机导出/导入语义;仅能引用的元数据通过`#using`(请参阅[#using 指令](../preprocessor/hash-using-directive-cpp.md))。  
  
 编译器现已更新，减少不必要的双重形式转换。 例如，带托管类型 （包括返回类型） 的签名的任何函数将隐式标记为`__clrcall`。 Double 转换 （thunk） 消除的详细信息，请参阅[ http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx)。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示如何双重形式转换。 当编译本机 (而无需 **/clr**)，对中的虚函数的调用`main`生成一次调用`T`的复制构造函数和析构函数的一个调用。 当虚函数声明与实现类似的行为 **/clr**和`__clrcall`。 但是，如果只需使用编译 **/clr**、 函数调用所生成复制构造函数的调用，但没有本机托管的转换 （thunk） 由于复制构造函数的另一次调用。  
  
### <a name="code"></a>代码  
  
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
  
### <a name="sample-output"></a>示例输出  
  
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
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 前面的示例演示了双重形式转换存在。 此示例演示其效果。 `for`循环调用虚函数，并且程序报表执行时间。 用编译了程序时，将报告最慢的时间 **/clr**。 编译而不在时报告的最快的时间 **/clr**或如果虚函数声明与`__clrcall`。  
  
### <a name="code"></a>代码  
  
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
  
### <a name="sample-output"></a>示例输出  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## <a name="see-also"></a>请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)