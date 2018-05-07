---
title: 如何： 使用 c + + 互操作封送 COM 字符串 |Microsoft 文档
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
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 918825dd6563f59167baa844b94edfc1033498a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>如何：使用 C++ 互操作封送 COM 字符串
本主题演示如何能够 BSTR （偏好在 COM 编程中的基本字符串格式） 传递从托管到非托管函数，反之亦然。 有关与其他字符串类型的互操作性，请参阅以下主题：  
  
-   [如何：使用 C++ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令来实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 仅包含非托管的函数的文件不需要使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将传递 BSTR （在 COM 编程中使用的字符串格式） 从托管到非托管函数。 调用托管函数使用<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>若要获取的 BSTR 表示形式的.NET System.String 内容的地址。 使用固定此指针[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)以确保在非托管的函数执行时，其物理地址在垃圾回收周期期间不发生更改。 垃圾回收器禁止移动直到内存[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)号超出范围。  
  
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
 下面的示例演示如何将传递 BSTR 从非托管代码向非托管函数。 接收托管的函数可以为 BSTR 使用中的字符串或使用<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>以将其转换为<xref:System.String>用于与其他托管函数。 由于在非托管堆上分配表示 BSTR 的内存，没有固定有必要，因为非托管堆上的没有进行垃圾回收。  
  
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