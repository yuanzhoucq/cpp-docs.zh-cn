---
title: "调用内联程序集内的 C++ 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 调用函数"
  - "函数调用, C++ 函数"
  - "函数调用, 在内联程序集中"
  - "函数 [C++], 在内联程序集中调用"
  - "内联程序集, 调用函数"
  - "Visual C++, 函数"
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 调用内联程序集内的 C++ 函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 `__asm` 块只能调用未重载的全局 C\+\+ 函数。  如果调用重载的全局 C\+\+ 函数或 C\+\+ 成员函数，则编译器会发出错误。  
  
 您还可以调用使用 **extern "C"** 链接声明的任何函数。  由于所有标准头文件都声明库函数具有 **extern "C"** 链接，这将允许 C\+\+ 程序中的 `__asm` 块调用 C 库函数。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)