---
title: "编译器警告（等级 4）C4702 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4702"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4702"
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 4）C4702
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法访问的代码  
  
 由于为 Visual Studio .NET 2003 进行的编译器一致性工作而生成此警告：无法访问的代码。  在编译器（后端）检测出无法访问的代码时，它将生成 C4702，这是 4 级警告。  
  
 为使代码在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，移出无法访问的代码或确保所有源代码都可通过某种执行流访问。  
  
## 示例  
 下面的示例生成 C4702。  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## 示例  
 在使用 **\/GX**、**\/EHc**、**\/EHsc** 或  **\/EHac** 编译并使用 extern C 函数时，代码可能变得无法访问，因为会假设不引发 extern C 函数，因此 catch 块不可访问。如果由于仍可引发函数而感觉此警告无效，则请使用 **\/EHa** 或 **\/EHs** 进行编译，具体使用哪个取决于所引发的异常。  
  
 有关更多信息，请参见 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)。  
  
 下面的示例生成 C4702。  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```