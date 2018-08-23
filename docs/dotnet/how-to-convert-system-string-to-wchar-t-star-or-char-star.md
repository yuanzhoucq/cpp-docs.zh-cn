---
title: '如何： 将 system:: string 转换为 wchar_t * 或 char * |Microsoft 文档'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- System::String, converting to char or wchar_t
- PtrToStringChars method
- System::String
- wchart type, converting System::String
- char data type, converting System::String to
ms.assetid: 385da01b-5649-4543-8076-e3e251243ff0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: db4b1955042b83b26ac8abfa9fa5b9b434d35a43
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33139756"
---
# <a name="how-to-convert-systemstring-to-wchart-or-char"></a>如何：将 System::String 转换为 wchar_t* 或 char*
你可以使用`PtrToStringChars`中要转换的 Vcclr.h<xref:System.String>到本机`wchar_t *`或`char *`。  由于 CLR 字符串内部是 Unicode，这始终返回宽的 Unicode 字符串指针。 你可以然后转换为宽字符串，如下面的示例中所示。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Hello  
Hello  
```  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)