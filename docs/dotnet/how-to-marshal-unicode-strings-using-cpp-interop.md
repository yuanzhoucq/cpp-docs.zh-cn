---
title: 如何：封送 Unicode 字符串使用C++互操作
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: 37b56834e000cff686557730252f3d425f642772
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400547"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>如何：封送 Unicode 字符串使用C++互操作

本主题演示了视觉对象的一个方面C++互操作性。 有关详细信息，请参阅[使用C++互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令以实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 文件仅包含非托管的函数无需使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。

本主题演示如何可以是 Unicode 字符串传递从托管到非托管函数，反之亦然。 有关与其他字符串类型进行互操作，请参阅以下主题：

- [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>示例

若要从托管到非托管函数传递一个 Unicode 字符串，可以使用 （在 Vcclr.h 中声明） 的 PtrToStringChars 函数中的托管的字符串的存储位置的内存访问。 因为此地址将传递给本机函数中，很重要，使用固定内存[pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)若要防止将其重定位的字符串数据，应垃圾回收周期发生时执行非托管的函数。

```
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>示例

下面的示例演示如何访问由非托管函数调用的托管函数中的 Unicode 字符串所需的数据封送处理。 托管的函数，在接收到本机的 Unicode 字符串，将其转换为托管的字符串使用<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>方法。

```
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
