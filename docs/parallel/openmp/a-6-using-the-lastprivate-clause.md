---
title: "A.6   Using the lastprivate Clause | Microsoft Docs"
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
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.6   Using the lastprivate Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

正确执行有时取决于循环最后一个迭代分配给变量的值。  此类程序必须列出所有此类变量与参数传递给 `lastprivate` 子句 \(在第 27 页\) 的[第2.7.2.3部分](../../parallel/openmp/2-7-2-3-lastprivate.md) ，以便变量的值是相同的，当循环顺序时地执行。  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 在前面的示例中， `i` 的值在并行区域末端将等于 `n–1`，在顺序大小写。