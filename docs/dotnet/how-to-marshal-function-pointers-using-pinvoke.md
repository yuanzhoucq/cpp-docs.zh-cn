---
title: "如何：使用 PInvoke 封送函数指针 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据封送处理 [C++], 回调和委托"
  - "互操作 [C++], 回调和委托"
  - "封送处理 [C++], 回调和委托"
  - "平台调用 [C++], 回调和委托"
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用 PInvoke 封送函数指针
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题说明在使用 .NET Framework P\/Invoke 功能与非托管函数进行交互操作时，如何使用托管委托取代函数指针。  但由于 P\/Invoke 几乎不提供编译时错误报告，不是类型安全的，实现起来也很单调，Visual C\+\+ 程序员最好转而使用 C\+\+ Interop 功能（如果可能）。  当将非托管 API 打包为 DLL，而源代码又不可用时，P\/Invoke 就成为唯一的选择。  另请参见下列主题：  
  
-   [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [如何：使用 C\+\+ 互操作封送回调和委托](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 可以使用托管委托取代本机函数指针来从托管代码中调用以函数指针作为参数的非托管 API。  编译器自动将委托作为函数指针封送给非托管函数，并插入必要的托管\/非托管转换代码。  
  
## 示例  
 下面的代码由一个非托管模块和一个托管模块组成。  非托管模块是一个 DLL，它定义名为 TakesCallback 并接受函数指针的函数。  此地址用于执行该函数。  
  
 托管模块定义将作为函数指针封送给本机代码的委托，并使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 特性向托管代码公开本机 TakesCallback 函数。  在主函数中，将创建该委托的一个实例并传递给 TakesCallback 函数。  该程序输出说明此函数由本机 TakesCallback 函数执行。  
  
 托管函数取消托管委托的垃圾回收，以阻止 .NET Framework 垃圾回收在本机函数执行时重新定位委托。  
  
 该托管模块使用 \/clr 进行编译，但 \/clr:pure 也适用。  
  
```  
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
  
```  
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
  
 请注意，使用传统的 \#include 指令不会向托管代码公开 DLL 的任何部分。  实际上，仅在运行时访问 DLL，所以在编译时将检测不到使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 导入的函数所存在的问题。  
  
## 请参阅  
 [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)