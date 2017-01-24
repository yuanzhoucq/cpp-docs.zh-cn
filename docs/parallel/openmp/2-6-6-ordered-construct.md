---
title: "2.6.6 ordered Construct | Microsoft Docs"
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
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.6 ordered Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

构造块后面 **排序** 指令按迭代在一个连续循环要执行的顺序执行。  **排序** 指令的语法如下所示:  
  
```  
#pragma omp ordered new-line  
   structured-block  
```  
  
 **排序** 指令必须在 **为** 或 **并行。** 构造中的动态区域。  **排序** 构造绑定 **为** 或 **并行。** 指令必须具有 **排序** 子句指定 [第2.4.1部分](../../parallel/openmp/2-4-1-for-construct.md) 如中所述在第 11. 页。  在 **为** 或 **并行。** 结构化执行与 **排序** 子句中， **排序** 构造按照其在循环的顺序执行要执行的顺序强执行。  
  
 为 **排序** 指令的限制如下所示:  
  
-   一个循环的迭代与 **为** 结构化不可多次执行相同的已排序的指令，因此，它无法执行多个 **排序** 指令。