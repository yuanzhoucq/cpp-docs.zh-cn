---
title: "3.1.9 omp_set_nested Function | Microsoft Docs"
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
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.9 omp_set_nested Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**omp\_set\_nested** 功能启用或禁用嵌套并行。  格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 如果 *嵌套* 的计算结果为 0，嵌套并行禁用，它是默认值，，并且当前线程序列化嵌套并行区域并执行。  *嵌套* 的计算结果为非零值，嵌套并行有效，并且，嵌套并行区域可以部署其他线程以形成嵌套团队。  
  
 该函数具有中描述的效果顶部，在调用从 **omp\_in\_parallel** 函数返回零程序的一部分。  如果从 **omp\_in\_parallel** 函数返回非零值程序的一部分调用，此功能的行为未定义。  
  
 这称为在 **OMP\_NESTED** 环境变量的优先级。  
  
 当嵌套并行启用时，用于执行的线程的数目嵌套并行区域实现中定义。  因此，，即使嵌套并行启用， OpenMP 兼容实现允许序列化嵌套并行区域。  
  
## 交叉引用:  
  
-   **OMP\_NESTED** 环境变量，请参见中的第 49 页的 [第4.4部分](../../parallel/openmp/4-4-omp-nested.md) 。  
  
-   **omp\_in\_parallel** 功能，请参见中的第 38 页的 [第3.1.6部分](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) 。