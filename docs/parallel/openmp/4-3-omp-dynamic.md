---
title: "4.3 OMP_DYNAMIC | Microsoft Docs"
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
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.3 OMP_DYNAMIC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_DYNAMIC** 环境变量启用或禁用线程数动态调整可用于并行区域的执行，除非动态调整通过调用 **omp\_set\_dynamic** 库实例显式启用或禁用。  其值必须是 **TRUE** 或 **错误**。  
  
 如果设置为 **TRUE**，对于执行并行区域使用线程的数目可能由种运行时环境调整以最佳利用系统资源。  如果设置为 **错误**，动态调整被禁用。  默认条件实现中定义。  
  
 示例：  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## 交叉引用:  
  
-   有关并行区域的更多信息，请参见在第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。  
  
-   **omp\_set\_dynamic** 功能，请参见中的第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。