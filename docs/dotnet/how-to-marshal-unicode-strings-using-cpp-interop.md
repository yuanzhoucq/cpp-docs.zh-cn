---
title: "如何：使用 C++ 互操作封送 Unicode 字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 互操作, 字符串"
  - "数据封送处理 [C++], 字符串"
  - "互操作 [C++], 字符串"
  - "封送处理 [C++], 字符串"
  - "Unicode, 封送处理字符串"
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ 互操作封送 Unicode 字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题演示 Visual C\+\+ 互操作性的一个方面。  有关详细信息，请参阅[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下面的代码示例使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指令在同一个文件中实现托管函数和非托管函数，但如果在不同的文件中定义这些函数，则它们将以同样的方式进行交互操作。  不需要使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 对仅包含非托管函数的文件进行编译。  
  
 此主题演示如何在托管函数和非托管函数之间传递 Unicode 字符串。  有关与其他字符串类型进行交互操作的信息，请参见以下主题：  
  
-   [如何：使用 C\+\+ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
## 示例  
 若要将 Unicode 字符串从托管函数传递给非托管函数，则可使用 PtrToStringChars 函数（在 Vcclr.h 中声明）访问存储托管字符串的内存。  由于要将此地址传递给本机函数，因此务必使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 固定内存，如果在非托管函数执行时出现垃圾回收周期，这样做可以防止字符串数据被重新定位。  
  
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
  
## 示例  
 下面的示例演示在非托管函数调用的托管函数中访问 Unicode 字符串时需要的数据封送处理。  一旦托管函数接收到本机 Unicode 字符串，就会使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 方法将其转换为托管字符串。  
  
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
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)