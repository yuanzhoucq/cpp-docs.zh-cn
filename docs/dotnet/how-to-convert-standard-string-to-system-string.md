---
title: "如何：将标准字符串转换为 System::String | Microsoft Docs"
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
  - "标准 C++ 库, 将字符串转换为 System::String"
  - "字符串转换 [C++], 标准 C++ 库字符串"
  - "字符串 [C++], 转换"
ms.assetid: 1fde79a0-9d0b-44e5-981b-e8f2676c199d
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将标准字符串转换为 System::String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题介绍如何将标准 C\+\+ 库字符串 \([\<string\>](../standard-library/string.md)\) 转换为 <xref:System.String>。  
  
## 示例  
  
```  
// convert_standard_string_to_system_string.cpp  
// compile with: /clr  
#include <string>  
#include <iostream>  
using namespace System;  
using namespace std;  
  
int main() {  
   string str = "test";  
   cout << str << endl;  
   String^ str2 = gcnew String(str.c_str());  
   Console::WriteLine(str2);  
  
   // alternatively  
   String^ str3 = gcnew String(str.c_str());  
   Console::WriteLine(str3);  
}  
```  
  
  **测试**  
**测试**  
**测试**   
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)