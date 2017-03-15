---
title: "2.5.1 parallel for Construct | Microsoft Docs"
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
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.5.1 parallel for Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**并行。** 指令是仅包含一个 **为** 指令的 **并行** 区域的快捷方式。  **并行。** 指令的语法如下所示:  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-line  
   for-loop  
```  
  
 此指令允许指令的 **并行** 的所有子句和 **为** 指令，但 `nowait` 子句，具有相同的含义和限制。  语义与显式指定 **为** 指令紧跟的 **并行** 指令相同。  
  
## 交叉引用:  
  
-   **并行** 指令，请参见中的第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。  
  
-   **为** 指令，请参见中的第 11. 页的 [第2.4.1部分](../../parallel/openmp/2-4-1-for-construct.md) 。  
  
-   数据特性子句，请参见中的第 25 页的 [2.7.2 Data\-Sharing Attribute Clauses](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 。