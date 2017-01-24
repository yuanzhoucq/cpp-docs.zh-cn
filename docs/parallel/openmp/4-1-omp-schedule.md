---
title: "4.1 OMP_SCHEDULE | Microsoft Docs"
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
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.1 OMP_SCHEDULE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_SCHEDULE** 仅适用于 **为** 和具有自定义类型 **运行时**的 **并行。** 指令。  计划类型和块范围所有此类循环的设置可以设置在运行时设置此环境变量设置为可识别的任何计划类型，并对选项 *chunk\_size*。  
  
 除了 **运行时**外，对于 **为** 和一个计划类型的 **并行。** 指令， **OMP\_SCHEDULE** 被忽略。  此环境变量的默认实现中定义。  如果选项 *chunk\_size* 设置，该值必须为正数的。  如果 *chunk\_size* 未设置为，值为 1，假设，但在 **静态** 计划。  对于 **静态** 时间表，默认块范围设置为线程的数目部件的循环迭代空间会应用于该循环。  
  
 示例：  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## 交叉引用:  
  
-   **为** 指令，请参见中的第 11. 页的 [第2.4.1部分](../../parallel/openmp/2-4-1-for-construct.md) 。  
  
-   **并行。** 指令，请参见中的第 16 页的 [第2.5.1部分](../../parallel/openmp/2-5-1-parallel-for-construct.md) 。