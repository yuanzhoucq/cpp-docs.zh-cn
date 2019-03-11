---
title: 如何：使用 PInvoke 封送函数指针
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: 031bda0f93d6a95aa3c774553aefca0647d0518c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742867"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>如何：使用 PInvoke 封送函数指针

本主题说明如何将托管的委托时与进行互操作非托管函数使用.NET Framework P/Invoke 功能来代替函数指针。 但是，Visual c + + 程序员是建议 （如果可能） 改为使用的 c + + 互操作功能，因为 P/Invoke 提供小的编译时错误报告，不是类型安全和可能乏善可陈来实现。 如果源代码不可用的非托管的 API 打包为 DLL，P/Invoke 是唯一的选项。 否则，请参阅以下主题：

- [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [如何：使用 C++ 互操作封送回调和委托](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

参数可以调用从托管代码与托管委托代替本机函数指针采用函数指针的非托管的 Api。 编译器会自动将封送到非托管函数作为函数指针的委托，并将插入托管/非托管的必要转换代码。

## <a name="example"></a>示例

下面的代码由非托管和托管的模块组成。 非托管的模块是一个 DLL，它定义一个名为 TakesCallback 接受函数指针的函数。 此地址用于执行函数。

托管的模块定义的委托作为函数指针的本机代码封送，并使用<xref:System.Runtime.InteropServices.DllImportAttribute>属性公开给托管代码的本机 TakesCallback 函数。 在主函数中，该委托的实例创建并传递给 TakesCallback 函数。 程序输出演示此函数获取由本机 TakesCallback 函数执行。

托管的函数禁止显示托管委托，以防止从本机函数执行时重新定位该委托的.NET Framework 垃圾回收垃圾回收。

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

请注意该 DLL 的任何部分公开给托管代码使用的传统 #include 指令。 实际上，该 DLL 在运行时访问，因此问题的函数导入与<xref:System.Runtime.InteropServices.DllImportAttribute>不会在编译时检测。

## <a name="see-also"></a>请参阅

[在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
