---
title: 如何：封送 COM 字符串使用C++互操作
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: e86cf0b3e57eda9a0f4fa5fe2337d0c42de5669f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780868"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>如何：封送 COM 字符串使用C++互操作

本主题演示如何能够 BSTR （偏好在 COM 编程中的基本字符串格式） 传递从托管到非托管函数，反之亦然。 有关与其他字符串类型进行互操作，请参阅以下主题：

- [如何：使用 C++ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令以实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 文件仅包含非托管的函数无需使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例演示如何将传递 BSTR （在 COM 编程中使用的字符串格式） 从托管到非托管函数。 调用托管函数使用<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>以获取.NET System.String 内容的 BSTR 表示形式的地址。 使用固定此指针[pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)以确保非托管的函数执行时，其物理地址在垃圾回收周期期间未发生更改。 禁止垃圾回收器移动到的内存[pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)超出范围。

```
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>示例

下面的示例演示如何将传递 BSTR 从非托管到非托管函数。 接收托管的函数可以使用与 BSTR 字符串中的，或使用<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>将其转换为<xref:System.String>与其他用于托管函数。 由于非托管堆上分配的内存表示 BSTR，没有固定有必要，因为非托管堆上的没有垃圾回收。

```
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
