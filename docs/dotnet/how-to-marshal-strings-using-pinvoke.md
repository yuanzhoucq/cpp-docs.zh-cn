---
title: "如何：使用 PInvoke 封送处理字符串 | Microsoft Docs"
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
  - "数据封送处理 [C++], 字符串"
  - "互操作 [C++], 字符串"
  - "封送处理 [C++], 字符串"
  - "平台调用 [C++], 字符串"
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用 PInvoke 封送处理字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题说明如何使用 CLR 字符串类型 System::String（它使用 .NET Framework 平台调用支持）调用可接受 C 样式字符串的本机函数。  Visual C\+\+ 程序员最好转而使用 C\+\+ Interop 功能（如果可能），因为 P\/Invoke 几乎不提供编译时错误报告，不是类型安全的，实现起来也很单调。  如果将非托管 API 打包为 DLL，并且源代码不可用，则 P\/Invoke 是唯一的选择，但还请参见[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 托管和非托管字符串在内存中布局不同，因此从托管函数向非托管函数传递字符串时需要使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性来指示编译器插入所需的转换机制，以正确且安全地封送字符串数据。  
  
 对于只使用内部数据类型的函数，则使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 声明进入本机函数的托管入口点，但对于传递字符串，则不将这些入口点定义为接受 C 样式字符串，而是改用 <xref:System.String> 类型的句柄。  这将提示编译器插入用于执行所需转换的代码。  对于接受字符串的非托管函数中的每个函数参数，应使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性来指示应将 String 对象作为 C 样式字符串封送至本机函数。  
  
## 示例  
 下面的代码由非托管模块和托管模块组成。  非托管模块是一个 DLL，它定义名为 TakesAString 并以 char\* 形式接受 C 样式 ANSI 字符串的函数。  托管模块是一个命令行应用程序，它导入 TakesAString 函数，但将其定义为接受托管的 System.String 而不接受 char\*。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性用于指示调用 TakesAString 时应如何封送托管字符串。  
  
 该托管模块使用 \/clr 进行编译，但 \/clr:pure 也适用。  
  
```  
// TraditionalDll2.cpp  
// compile with: /LD /EHsc  
#include <windows.h>  
#include <stdio.h>  
#include <iostream>  
  
using namespace std;  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAString(char*);  
}  
  
void TakesAString(char* p) {  
   printf_s("[unmanaged] %s\n", p);  
}  
```  
  
```  
// MarshalString.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL  
{  
   [DllImport("TraditionalDLL2.dll")]  
      static public void   
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);  
};  
  
int main() {  
   String^ s = gcnew String("sample string");  
    Console::WriteLine("[managed] passing managed string to unmanaged function...");  
   TraditionalDLL::TakesAString(s);  
   Console::WriteLine("[managed] {0}", s);  
}  
```  
  
 此技术将引起在非托管堆上构造字符串的副本，所以本机函数对字符串所做的更改将不会在字符串的托管副本中得到反映。  
  
 请注意，DLL 的任何部分都不通过传统的 \#include 指令向托管代码公开。  实际上，只在运行时访问 DLL，所以在编译时无法检测到使用 `DllImport` 导入的函数所存在的问题。  
  
## 请参阅  
 [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)