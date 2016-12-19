---
title: "2.5.2 parallel sections Construct | Microsoft Docs"
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
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.5.2 parallel sections Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**并行部分** 指令指定只包含一个 **部分** 指令的 **并行** 区域提供一个快捷方式。  语义与显式指定 **部分** 指令紧跟的 **并行** 指令相同。  **并行部分** 指令的语法如下所示:  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-line  
      structured-block  ]  
   ...  
}  
```  
  
 *子句* 可以是 **并行** 和 **部分** 指令接受的一个子句，但 **nowait** 子句。  
  
## 交叉引用:  
  
-   **并行** 指令，请参见中的第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。  
  
-   **部分** 指令，请参见中的第 14 页的 [第2.4.2部分](../../parallel/openmp/2-4-2-sections-construct.md) 。