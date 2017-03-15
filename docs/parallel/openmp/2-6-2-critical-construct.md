---
title: "2.6.2 critical Construct | Microsoft Docs"
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
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.2 critical Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**重要** 指令标识限制关联的执行构造每个块。一个线程的构造。  **重要** 指令的语法如下所示:  
  
```  
#pragma omp critical [(name)]  new-line  
   structured-block  
```  
  
 一个选项卡名称可以用于标识临界区域。  用于的标识符标识一个重要区域有外部链接和于标签、标记、成员和普通标识符使用的命名空间的命名空间。  
  
 线程在一个重要区域的等待，直到其他线程不执行重要区域 \(中的任意位置程序\) 具有相同的名称。  所有未命名的 **重要** 指令映射到同一个未指定的名称。