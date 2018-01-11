---
title: "如何： 使用 PInvoke 封送函数指针 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cf7f23ea9337b499d4ec80b19e3104074429cc71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>如何：使用 PInvoke 封送函数指针
本主题说明如何将托管的委托时与进行互操作非托管函数使用.NET Framework P/Invoke 功能可用于代替函数指针。 但是，Visual c + + 程序员是建议 （如果可能） 改为使用 c + + 互操作功能，因为 P/Invoke 提供很少的编译时错误报告，不是类型安全和可能乏善可陈实现的。 如果非托管的 API 打包为的 DLL 的源代码不可用，P/Invoke 是唯一的选项。 否则，请参阅以下主题：  
  
-   [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [如何：使用 C++ 互操作封送回调和委托](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 需要函数指针，如下图所可以从代替本机函数指针的托管委托的托管代码调用自变量的非托管的 Api。 编译器自动封送到非托管函数作为函数指针的委托，并将插入的代码需要托管/非托管的转换。  
  
## <a name="example"></a>示例  
 下面的代码由非托管和的托管的模块组成。 非托管的模块是一个 DLL，它定义一个名为 TakesCallback 接受函数指针的函数。 此地址用于执行该函数。  
  
 托管的模块定义一个委托，封送到本机代码作为函数指针并使用<xref:System.Runtime.InteropServices.DllImportAttribute>属性公开给托管代码的本机 TakesCallback 函数。 在主函数中，委托的一个实例是创建并传递给 TakesCallback 函数。 程序输出演示此函数获取执行者本机 TakesCallback 函数。  
  
 托管的函数取消阻止从本机函数执行时重新定位该委托的.NET Framework 垃圾回收的托管委托的垃圾回收。  
  
 托管的模块编译 /clr，但 /clr: pure 工作原理以及。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
```cpp  
// TraditionalDll5.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   /* Declare an unmanaged function type that takes two int arguments  
      Note the use of __stdcall for compatibility with managed code */  
   typedef int (__stdcall *CALLBACK)(int);  
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);  
}  
  
int TakesCallback(CALLBACK fp, int n) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n);  
}  
```  
  
```cpp  
// MarshalDelegate.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
public delegate int GetTheAnswerDelegate(int);  
public value struct TraditionalDLL {  
   [DllImport("TraditionalDLL5.dll")]  
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);  
};  
  
int GetNumber(int n) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
   return x + n;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TraditionalDLL::TakesCallback(fp, 42);  
}  
```  
  
 请注意，对使用传统的托管代码公开的 DLL 没有一部分 #include 指令。 事实上，DLL 在运行时访问仅，因此问题与函数导入具有<xref:System.Runtime.InteropServices.DllImportAttribute>将不会在编译时检测。  
  
## <a name="see-also"></a>请参阅  
 [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)