---
title: "如何：使用 C++ 互操作封送 COM 字符串 | Microsoft Docs"
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
  - "COM [C++], 封送处理字符串"
  - "数据封送处理 [C++], 字符串"
  - "互操作 [C++], 字符串"
  - "封送处理 [C++], 字符串"
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ 互操作封送 COM 字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题演示如何在托管函数和非托管函数之间传递 BSTR（在 COM 编程中非常受欢迎的基本字符串格式）。  有关与其他字符串类型进行交互操作的信息，请参见以下主题：  
  
-   [如何：使用 C\+\+ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 下面的代码示例使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指令在同一个文件中实现托管函数和非托管函数，但如果在不同的文件中定义这些函数，则它们将以同样的方式进行交互操作。  不需要使用 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 对仅包含非托管函数的文件进行编译。  
  
## 示例  
 下面的示例演示如何将 BSTR（COM 编程中使用的一种字符串格式）从托管函数传递到非托管函数。  执行调用的托管函数使用 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 获取 .NET System.String 内容 BSTR 表示形式的地址。  使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 固定此指针，以确保执行该非托管函数时，其物理地址在垃圾回收周期期间不发生更改。  在 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 超出范围之前，将禁止垃圾回收器移动内存。  
  
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
  
## 示例  
 下面的示例演示如何将 BSTR 从非托管函数传递到托管函数。  进行接收的托管函数可以将传入的字符串作为 BSTR 使用，也可以使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 将其转换为 <xref:System.String>，以便与其他托管函数一起使用。  由于表示 BSTR 的内存是在非托管堆上分配的，而在非托管堆上没有垃圾回收，因此不需要进行固定。  
  
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
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)