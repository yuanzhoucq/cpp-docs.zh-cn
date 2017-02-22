---
title: "堆栈使用 | Microsoft Docs"
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
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 堆栈使用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所有超出当前 RSP 地址的内存均视为易失的：操作系统或调试器可能会在用户调试会话或中断处理程序期间覆盖此内存。  因此，通常必须在尝试对堆栈帧值进行读写之前对 RSP 进行设置。  
  
 本节讨论局部变量的堆栈空间分配以及 **alloca** 内部函数。  
  
-   [堆栈分配](../build/stack-allocation.md)  
  
-   [动态参数堆栈区域构造](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [函数类型](../build/function-types.md)  
  
-   [malloc 对齐](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## 请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)