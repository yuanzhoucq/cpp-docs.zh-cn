---
title: "链接器工具警告 LNK4217 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4217"
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 链接器工具警告 LNK4217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在函数“function”中导入了本地定义的符号“symbol”  
  
 即使符号是本地定义的，仍为符号指定了 [\_\_declspec\(dllimport\)](../../cpp/dllexport-dllimport.md)。  移除 `__declspec` 修饰符以解决此警告。  
  
 `symbol` 是在映像内定义的符号名称。  `function` 是导入符号的函数。  
  
 使用选项 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 进行编译时不会出现此警告。  
  
 当尝试将两个模块链接在一起时，也将发生 LNK4217，此时，应改用第一个模块的导入库对第二个模块进行编译。  
  
```  
// LNK4217.cpp  
// compile with: /LD  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 然后，  
  
```  
// LNK4217b.cpp  
// compile with: /c  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 尝试链接这两个模块将导致 LNK4217，请用第一个示例的导入库对第二个示例进行编译来消除此问题。