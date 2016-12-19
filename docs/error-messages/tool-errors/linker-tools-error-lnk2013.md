---
title: "链接器工具错误 LNK2013 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2013"
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

链接地址信息类型 fixup 溢出。目标“symbol name”超出范围  
  
 链接器无法使必要的地址或偏移量适合给定指令，因为目标符号距离指令的位置太远。  
  
 通过创建多个图像或通过使用 [\/ORDER](../../build/reference/order-put-functions-in-order.md) 选项使指令和目标靠近，可以解决此问题。  
  
 当符号名为用户定义符号（而不是编译器生成的符号）时，还可以尝试下列操作以解决该错误：  
  
-   将静态函数更改为非静态。  
  
-   重命名包含静态函数的代码段，使其与调用方同名。  
  
 使用 `DUMPBIN /SYMBOLS`，可以查看一个函数是否为静态函数。