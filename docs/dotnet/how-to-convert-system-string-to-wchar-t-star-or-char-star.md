---
title: "如何：将 System::String 转换为 wchar_t* 或 char* | Microsoft Docs"
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
  - "char 数据类型, 从 System::String 转换"
  - "PtrToStringChars 方法"
  - "System::String"
  - "System::String, 转换为 char 或 wchar_t"
  - "wchart 类型, 转换 System::String"
ms.assetid: 385da01b-5649-4543-8076-e3e251243ff0
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将 System::String 转换为 wchar_t* 或 char*
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以在 Vcclr.h 中使用 `PtrToStringChars` 将 <xref:System.String> 转换为本机 `wchar_t *` 或 `char *`。由于 CLR 字符串为内部 Unicode，因此这样通常会返回一个 Unicode 宽字符串指针。  然后可以将其转换为宽字符串，如下面的示例中所示。  
  
## 示例  
  
```  
// convert_string_to_wchar.cpp  
// compile with: /clr  
#include < stdio.h >  
#include < stdlib.h >  
#include < vcclr.h >  
  
using namespace System;  
  
int main() {  
   String ^str = "Hello";  
  
   // Pin memory so GC can't move it while native function is called  
   pin_ptr<const wchar_t> wch = PtrToStringChars(str);  
   printf_s("%S\n", wch);  
  
   // Conversion to char* :  
   // Can just convert wchar_t* to char* using one of the   
   // conversion functions such as:   
   // WideCharToMultiByte()  
   // wcstombs_s()  
   // ... etc  
   size_t convertedChars = 0;  
   size_t  sizeInBytes = ((str->Length + 1) * 2);  
   errno_t err = 0;  
   char    *ch = (char *)malloc(sizeInBytes);  
  
   err = wcstombs_s(&convertedChars,   
                    ch, sizeInBytes,  
                    wch, sizeInBytes);  
   if (err != 0)  
      printf_s("wcstombs_s  failed!\n");  
  
    printf_s("%s\n", ch);  
}  
```  
  
  **Hello**  
**Hello**   
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)