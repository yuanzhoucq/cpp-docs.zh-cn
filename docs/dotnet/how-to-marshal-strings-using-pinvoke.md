---
title: 如何：使用 PInvoke 封送处理字符串
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: e89177261aa32d34ea392030078d4088ea61e2a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545221"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>如何：使用 PInvoke 封送处理字符串

本主题说明如何使用 CLR 字符串类型 System：： String （使用 .NET Framework 平台调用支持）来调用接受 C 样式字符串的本机函数。 鼓励C++视觉程序员改用C++互操作功能（如有可能），因为 P/Invoke 提供的编译时错误报告很少，并且不是类型安全的，并且可能会单调地实现。 如果将非托管 API 打包为 DLL，并且源代码不可用，则 P/Invoke 是唯一的选项，但也可参阅[ C++使用互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

托管和非托管字符串在内存中布局不同，因此将字符串从托管函数传递到非托管函数要求 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性指示编译器插入所需的转换机制，以便正确、安全地封送处理字符串数据。

与仅使用内部数据类型的函数一样，<xref:System.Runtime.InteropServices.DllImportAttribute> 用于将托管入口点声明为本机函数，但要传递字符串，而不是将这些入口点定义为采用 C 样式字符串，可以改为使用 <xref:System.String> 类型的句柄。 这会提示编译器插入执行所需转换的代码。 对于采用字符串的非托管函数中的每个函数参数，应使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性来指示应将字符串对象作为 C 样式字符串封送到本机函数。

封送拆收器会将对非托管函数的调用包装到隐藏包装例程中，该例程将托管字符串固定并复制到非托管上下文中的本地分配字符串中，然后将该字符串传递到非托管函数。 当非托管函数返回时，包装器会删除资源，如果该资源在堆栈上，则在包装超出范围时将其回收。 非托管函数不负责此内存。 非托管代码仅在由其自身的 CRT 设置的堆中创建和删除内存，因此使用不同 CRT 版本的封送处理程序决不会出现问题。

如果非托管函数返回字符串作为返回值或输出参数，则封送拆收器会将其复制到新的托管字符串，然后释放内存。 有关详细信息，请参阅[默认封送处理行为](/dotnet/framework/interop/default-marshaling-behavior)和[用平台调用封送数据](/dotnet/framework/interop/marshaling-data-with-platform-invoke)。

## <a name="example"></a>示例

下面的代码由一个非托管模块和一个托管模块组成。 非托管模块是一个 DLL，它定义了一个名为 TakesAString 的函数，该函数接受以 char * 形式表示的 C 样式的 ANSI 字符串。 托管模块是一个命令行应用程序，该应用程序导入 TakesAString 函数，但将其定义为采用托管系统字符串，而不是使用 char\*。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 特性用于指示在调用 TakesAString 时应如何封送托管字符串。

```cpp
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

```cpp
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

此方法会导致在非托管堆上构造字符串的副本，因此，由本机函数对字符串所做的更改不会反映在该字符串的托管副本中。

请注意，DLL 的任何部分都不会通过传统的 #include 指令公开给托管代码。 事实上，DLL 仅在运行时进行访问，因此在编译时不会检测到用 `DllImport` 导入的函数的问题。

## <a name="see-also"></a>另请参阅

[在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
