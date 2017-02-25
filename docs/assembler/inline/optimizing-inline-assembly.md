---
title: "优化内联程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 优化"
  - "内联程序集, 优化"
  - "优化, 内联程序集"
  - "优化性能, 内联程序集"
  - "存储, 在内联程序集中优化"
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 优化内联程序集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 如果函数中存在 `__asm` 块，则会在多个方面影响优化。  首先，编译器不会尝试优化 `__asm` 块本身。  您在汇编语言中编写的内容就是您获得的内容。  第二，存在 `__asm` 块将影响寄存器变量存储。  如果寄存器的内容将被 `__asm` 块更改，编译器将避免在 `__asm` 块中注册变量。  最后，其他某些函数范围的优化将受函数中包含的汇编语言的影响。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)