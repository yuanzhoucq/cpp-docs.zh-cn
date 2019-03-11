---
title: 如何：使用 PInvoke 封送数组
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 60b49135928e3dadffc2a3c7a422646d2f3a768d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752306"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>如何：使用 PInvoke 封送数组

本主题说明如何本机函数的可调用使用 CLR 字符串类型的 C 样式字符串接受<xref:System.String>使用.NET Framework 平台调用支持。 建议改为使用的 c + + 互操作功能 （如果可能） visual c + + 程序员的因为 P/Invoke 提供小的编译时错误报告，不是类型安全和可能乏善可陈来实现。 如果源代码不可用的非托管的 API 打包为 DLL，P/Invoke 是唯一的选项 (否则，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md))。

## <a name="example"></a>示例

因为本机和托管数组的布局方式以不同的方式在内存中，在托管/非托管边界之间成功传递需要进行转换或封送处理。 本主题演示如何简单 (blitable) 项的数组将传递到本机函数从托管代码。

为 true 的托管/非托管数据封送处理一般情况下，如<xref:System.Runtime.InteropServices.DllImportAttribute>属性用于创建将使用每个本机函数的托管的入口点。 在采用数组作为自变量，函数的情况下<xref:System.Runtime.InteropServices.MarshalAsAttribute>必须也使用属性来向编译器指定的数据将封送。 在以下示例中，<xref:System.Runtime.InteropServices.UnmanagedType>枚举用于指示将作为 C 样式数组封送托管的数组。

下面的代码由非托管和托管的模块组成。 非托管的模块是一个 DLL，它定义了一个函数接受一个整数数组。 第二个模块是一个托管的命令行应用程序导入此函数，但定义根据托管数组，并使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>特性以指定应将数组转换为本机数组时调用。

使用 /clr 编译的托管的模块。

```cpp
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

```cpp
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

请注意该 DLL 的任何部分公开为通过传统的托管代码 #include 指令。 事实上，因为仅在运行时访问该 DLL，则问题的函数导入与<xref:System.Runtime.InteropServices.DllImportAttribute>不会在编译时检测。

## <a name="see-also"></a>请参阅

[在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
