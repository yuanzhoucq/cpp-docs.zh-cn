---
title: 双形式转换 （c + +） |Microsoft Docs
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
ms.openlocfilehash: 3e37b3b7fc477de0bdbeb00a15ebd86e6c44d25c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216632"
---
# <a name="double-thunking-c"></a>双重 Thunk (C++)
双重形式转换是指可以体验中托管的上下文调用 Visual c + + 托管函数和程序执行的函数调用调用托管的函数调用函数的本机入口点时的性能降低。 本主题介绍了双重形式出现的位置和如何避免以提高性能。  
  
## <a name="remarks"></a>备注  
 默认情况下，使用编译时 **/clr**，托管函数的定义会导致编译器生成一个托管的入口点和一个本机入口点。 这允许从本机和托管的调用站点调用托管的函数。 但是，当存在的本机入口点，它可以是对函数的所有调用的入口点。 如果管理调用的函数，本机入口点将调用托管的入口点。 实际上，需要两个调用来调用该函数 （因此，双形式转换）。 例如，通过本机入口点始终调用虚函数。  
  
 一种解决方法是告知编译器不生成托管的函数，一个本机入口点，该函数将仅调用从托管上下文中，通过使用[__clrcall](../cpp/clrcall.md)调用约定。  
  
 同样，如果导出 ([dllexport、 dllimport](../cpp/dllexport-dllimport.md)) 托管的函数，生成一个本机入口点和任何函数导入，并调用该函数将调用通过本机入口点。 若要避免双重形式转换在此情况下，不要使用本机导出/导入语义;只需引用通过元数据`#using`(请参阅[#using 指令](../preprocessor/hash-using-directive-cpp.md))。  
  
 编译器已更新，以减少不必要的双重形式转换。 例如，使用托管类型 （包括返回类型） 的签名中的任何函数会隐式标记为`__clrcall`。 双精度的转换 （thunk） 消除的详细信息，请参阅[ https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx)。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例演示了双重形式转换。 本机编译时 (而无需 **/clr**)，对中的虚拟函数调用`main`生成一次调用`T`的复制构造函数和析构函数调用一次。 使用声明的虚函数时，才能够达到类似的行为 **/clr**和`__clrcall`。 但是，只需使用编译时 **/clr**，函数调用生成复制构造函数的调用，但由于本机托管转换 （thunk） 的复制构造函数的另一个调用。  
  
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
 前面的示例所示双重形式的存在。 此示例演示其效果。 `for`循环调用虚函数和程序的报表执行时间。 程序编译时，会报告的速度最慢时间 **/clr**。 无需编译时报告的最快时间 **/clr**或者如果该虚拟函数声明与`__clrcall`。  
  
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