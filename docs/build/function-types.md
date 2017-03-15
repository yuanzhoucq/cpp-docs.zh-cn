---
title: "函数类型 | Microsoft Docs"
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
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 函数类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

基本上有两种函数类型。  需要堆栈帧的函数称为帧函数。  不需要堆栈帧的函数称为叶函数。  
  
 帧函数是分配堆栈空间、调用其他函数、保存非易失寄存器或使用异常处理的函数。  它还要求有一个函数表项。  帧函数需要有 Prolog 和 Epilog。  帧函数可以动态分配堆栈空间并采用帧指针。  帧函数可以全权处理此调用标准的所有功能。  
  
 如果帧函数不调用另一个函数，那么就不需要用它来对齐堆栈（请参考 [堆栈分配](../build/stack-allocation.md) 一节）。  
  
 叶函数不需要函数表项。  它不能调用任何函数，不能分配空间，也不能保存任何非易失寄存器。  执行叶函数时，允许不对齐堆栈。  
  
## 请参阅  
 [堆栈使用](../build/stack-usage.md)