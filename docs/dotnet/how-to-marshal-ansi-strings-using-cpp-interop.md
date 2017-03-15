---
title: "如何：使用 C++ 互操作封送 ANSI 字符串 | Microsoft Docs"
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
  - "ANSI [C++], 封送处理字符串"
  - "C++ 互操作, 字符串"
  - "数据封送处理 [C++], 字符串"
  - "互操作 [C++], 字符串"
  - "封送处理 [C++], 字符串"
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ 互操作封送 ANSI 字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题演示如何使用 C\+\+ Interop 传递 ANSI 字符串，但是 .NET Framework <xref:System.String> 采用 Unicode 格式表示字符串，因此转换为 ANSI 是一个附加步骤。  要实现与其他字符串类型的交互操作，请参见下列主题：  
  
-   [如何：使用 C\+\+ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 下面的代码示例使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指令在同一个文件中实现托管函数和非托管函数，但如果在不同的文件中定义这些函数，则它们将以同样的方式进行交互操作。  由于不需要使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 编译仅包含非托管函数的文件，因此这些文件可以保留它们的性能特性。  
  
## 示例  
 该示例演示如何使用 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 将 ANSI 字符串从托管函数传递给非托管函数。  执行转换后，此方法在非托管堆中分配内存并返回地址。  这意味着不需要固定（因为 GC 堆中的内存没有传递给非托管函数），并且从 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 返回的 IntPtr 必须显式释放，否则会导致内存泄漏。  
  
```  
// MarshalANSI1.cpp  
// compile with: /clr  
#include <iostream>  
#include <stdio.h>  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(const char* p) {  
   printf_s("(native) received '%s'\n", p);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = gcnew String("sample string");  
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);  
   const char* str = static_cast<const char*>(ip.ToPointer());  
  
   Console::WriteLine("(managed) passing string...");  
   NativeTakesAString( str );  
  
   Marshal::FreeHGlobal( ip );  
}  
```  
  
## 示例  
 下面的示例演示访问由非托管函数调用的托管函数中的 ANSI 字符串所需的数据封送处理。  托管函数在接收到本机字符串时，可以直接使用该字符串，也可以按所示方式使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> 方法将其转换为托管字符串。  
  
```  
// MarshalANSI2.cpp  
// compile with: /clr  
#include <iostream>  
#include <vcclr.h>  
  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedStringFunc(char* s) {  
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));  
   Console::WriteLine("(managed): received '{0}'", ms);  
}  
  
#pragma unmanaged  
  
void NativeProvidesAString() {  
   cout << "(native) calling managed func...\n";  
   ManagedStringFunc("test string");  
}  
  
#pragma managed  
  
int main() {  
   NativeProvidesAString();  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)