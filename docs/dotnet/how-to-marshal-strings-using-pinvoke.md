---
title: 如何： 使用 PInvoke 封送字符串 |Microsoft Docs
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
ms.openlocfilehash: d917228b1972715c291d84625cc684fc9de5b998
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396371"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>如何：使用 PInvoke 封送处理字符串

本主题说明如何将纯函数接受可以使用 CLR 字符串调用 C 样式字符串键入 system:: string 使用.NET Framework 平台调用支持。 建议改为使用的 c + + 互操作功能 （如果可能） visual c + + 程序员的因为 P/Invoke 提供小的编译时错误报告，不是类型安全和可能乏善可陈来实现。 如果非托管的 API 打包为 DLL，并且源代码不可用，P/Invoke 是唯一选项; 但否则请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

托管和非托管字符串中列出了不同内存，因此传递字符串从托管代码流向非托管函数需要<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性来指示编译器插入的封送处理字符串数据的所需的转换机制正确且安全地。

与仅使用内部数据类型，函数一样<xref:System.Runtime.InteropServices.DllImportAttribute>用于为本机函数，但对于传递字符串，而不是这些入口点定义为采用 C 样式字符串，句柄声明托管的入口点<xref:System.String>类型可以改为使用。 这会提示编译器插入代码来执行所需的转换。 采用一个字符串，非托管函数中每个函数参数的<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性应该用于指示应为 C 样式字符串形式的本机函数封送处理字符串对象。

## <a name="example"></a>示例

下面的代码由非托管和托管的模块组成。 非托管的模块是定义一个名为 TakesAString 接受 C 样式 ANSI 字符串形式的 char * 函数的 DLL。 托管的模块是命令行应用程序导入 TakesAString 函数，但定义为采用托管的 System.String 而不是 char\*。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>特性用于指示如何托管的字符串应封送调用 TakesAString 时。

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

此方法会导致在非托管堆上，以便将本机函数的字符串所做的更改不会反映在托管副本的字符串构造的字符串的副本。

请注意该 DLL 的任何部分公开为通过传统的托管代码 #include 指令。 实际上，该 DLL 在运行时访问，因此问题的函数导入与`DllImport`不会在编译时检测。

## <a name="see-also"></a>请参阅

[在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)