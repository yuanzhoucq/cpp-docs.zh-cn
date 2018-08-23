---
title: 如何： 使用 PInvoke 封送字符串 |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a377e7074e72693a1a63e392c64a6d60c5995b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133202"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>如何：使用 PInvoke 封送处理字符串
本主题说明如何本机接受 C 样式字符串可以使用的 CLR 字符串来调用的函数键入 system:: string 使用.NET Framework 平台调用支持。 Visual c + + 程序员人员最好 （如果可能） 改为使用 c + + 互操作功能，因为 P/Invoke 提供很少的编译时错误报告，不是类型安全和可能乏善可陈来实现。 如果非托管的 API 打包为一个 DLL，并且源代码不可用，P/Invoke 是唯一的选项中，但否则看到[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 托管和非托管字符串中列出了不同内存，因此传递字符串从托管代码流向非托管函数要求<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性来指示编译器将插入封送字符串数据的所需的转换机制正确且安全地。  
  
 与只使用内部数据类型，函数一样<xref:System.Runtime.InteropServices.DllImportAttribute>用于声明托管的入口点到本机函数中，但对于传递字符串，而不是这些入口点定义为采用 C 样式字符串的句柄<xref:System.String>类型可以改用。 这将提示编译器将插入代码来执行所需的转换。 对于接受一个字符串，非托管函数中的每个函数参数<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性应该用于指示的字符串对象，应封送到的本机功能与 C 样式字符串。  
  
## <a name="example"></a>示例  
 下面的代码由非托管模块和托管的模块组成。 非托管的模块是一个 DLL，它定义一个名为 TakesAString 接受的 char * 窗体中的 C 样式 ANSI 字符串的函数。 托管的模块是一个命令行应用程序，将导入 TakesAString 函数，但定义为采用托管的 System.String 而不是 char\*。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>特性用于指示如何的托管的字符串应封送调用 TakesAString 时。  
  
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
  
 此方法将使得要在非托管堆上构造，以便由本机函数对字符串所做的更改不会反映在托管副本的字符串的字符串的副本。  
  
 请注意该 DLL 没有部分对通过传统的托管代码公开 #include 指令。 事实上，DLL 在运行时访问仅，因此问题与函数导入具有`DllImport`将不会在编译时检测。  
  
## <a name="see-also"></a>请参阅  
 [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)