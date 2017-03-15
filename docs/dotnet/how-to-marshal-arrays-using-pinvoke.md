---
title: "如何：使用 PInvoke 封送数组 | Microsoft Docs"
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
  - "数据封送处理 [C++], 数组"
  - "互操作 [C++], 数组"
  - "封送处理 [C++], 数组"
  - "平台调用 [C++], 数组"
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：使用 PInvoke 封送数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题说明如何使用 CLR 字符串类型 <xref:System.String> 调用接受 C 样式字符串的本机函数（通过使用 .NET Framework 平台调用支持）。  Visual C\+\+ 程序员最好转而使用 C\+\+ Interop 功能（如果可能），因为 P\/Invoke 几乎不提供编译时错误报告，不是类型安全的，实现起来也很单调。  当将非托管 API 打包为 DLL，而源代码又不可用时，P\/Invoke 就成为了唯一的选择（另请参见[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)）。  
  
## 示例  
 由于本机数组和托管数组在内存中以不同的方式布局，因此在跨托管\/非托管边界成功传递这些数组时需要进行转换或封送处理。  本主题演示如何将简单 \(blitable\) 项数组传递给托管代码中的本机函数。  
  
 对于托管\/非托管数据封送处理，通常将 <xref:System.Runtime.InteropServices.DllImportAttribute> 特性用于为将要使用的每个本机函数创建托管入口点。  在使用采用数组作为参数的函数时，还必须使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性为编译器指定对数据进行封送处理的方式。  在下面的示例中，使用 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举指示托管数组将被封送为 C 样式的数组。  
  
 下面的代码由一个非托管模块和一个托管模块组成。  非托管模块是一个 DLL，用于定义接受整数数组的函数。  第二个模块是一个托管命令行应用程序（该应用程序导入此函数，但以托管数组的方式定义此函数），并使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性指定调用时应该将数组转换为本机数组。  
  
 该托管模块使用 \/clr 进行编译，但 \/clr:pure 也适用。  
  
```  
// TraditionalDll4.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);  
}  
  
void TakesAnArray(int len, int a[]) {  
   printf_s("[unmanaged]\n");  
   for (int i=0; i<len; i++)  
      printf("%d = %d\n", i, a[i]);  
}  
```  
  
```  
// MarshalBlitArray.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL4.dll")]  
   static public void TakesAnArray(  
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);  
};  
  
int main() {  
   array<int>^ b = gcnew array<int>(3);  
   b[0] = 11;  
   b[1] = 33;  
   b[2] = 55;  
   TraditionalDLL::TakesAnArray(3, b);  
  
   Console::WriteLine("[managed]");  
   for (int i=0; i<3; i++)  
      Console::WriteLine("{0} = {1}", i, b[i]);  
}  
```  
  
 请注意，DLL 中的任何部分都不会通过传统的 \#include 指令向托管代码公开。  实际上，由于 DLL 仅在运行时进行访问，因此编译时不会检测到使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 导入的函数的相关问题。  
  
## 请参阅  
 [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)