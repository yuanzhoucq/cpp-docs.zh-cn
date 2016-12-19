---
title: "3.1.10 omp_get_nested Function | Microsoft Docs"
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
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.10 omp_get_nested Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_nested` 函数返回非零值，如果嵌套并行启用和 0，则禁用。  有关嵌套并行的更多信息，请参见有关第 40 页的第 3.1.9 部分。  格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 如果实现不实现嵌套并行，此函数始终返回 0。