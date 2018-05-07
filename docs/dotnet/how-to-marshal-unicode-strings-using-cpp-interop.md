---
title: 如何： 使用 c + + 互操作封送 Unicode 字符串 |Microsoft 文档
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
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5290958a55c61dd55adac0f182af7163896d694
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>如何：使用 C++ 互操作封送 Unicode 字符串
本主题演示 Visual c + + 互操作性的一个的方面。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令来实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 仅包含非托管的函数的文件不需要使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 本主题演示如何能够 Unicode 字符串传递从托管到非托管函数，反之亦然。 有关与其他字符串类型的互操作性，请参阅以下主题：  
  
-   [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
## <a name="example"></a>示例  
 若要将从托管的 Unicode 字符串传递到非托管函数，可以使用 PtrToStringChars 函数 （在 Vcclr.h 中声明） 的托管的字符串的存储位置的内存中的访问。 由于此地址将传递给本机函数中，很重要，使用固定内存[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)以防止被重新定位的字符串数据，应垃圾回收周期发生时非托管的函数执行。  
  
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
 下面的示例演示如何访问由非托管函数调用托管函数中的 Unicode 字符串所需的数据封送处理。 托管的函数，在接收到本机的 Unicode 字符串，将其转换到非托管的字符串使用<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>方法。  
  
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