---
title: 如何：使用 C++ 互操作封送 Unicode 字符串
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: f666e52b604e4713f02cb14744ac12a0407366a3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544885"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>如何：使用 C++ 互操作封送 Unicode 字符串

本主题演示了一个可视化C++互操作性方面。 有关详细信息，请[参阅C++ Using 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下面的代码示例使用[托管的非托管](../preprocessor/managed-unmanaged.md)#pragma 指令来实现同一文件中的托管和非托管函数，但如果在单独的文件中定义，则这些函数将以相同的方式进行交互。 仅包含非托管函数的文件不需要用[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译。

本主题演示如何将 Unicode 字符串从托管函数传递到非托管函数，反之亦然。 若要与其他字符串类型互操作，请参阅以下主题：

- [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>示例

若要将 Unicode 字符串从托管函数传递到非托管函数，可使用 PtrToStringChars 函数（在 Vcclr 中声明）访问存储托管字符串的内存。 由于此地址将传递给本机函数，因此，内存必须固定[pin_ptr （C++/cli）](../extensions/pin-ptr-cpp-cli.md) ，以防止字符串数据被重定位，这在非托管函数执行时是否会发生垃圾回收循环。

```cpp
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

下面的示例演示了在非托管函数调用的托管函数中访问 Unicode 字符串所需的数据封送处理。 托管函数接收本机 Unicode 字符串后，将使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 方法将其转换为托管字符串。

```cpp
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

## <a name="see-also"></a>另请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
