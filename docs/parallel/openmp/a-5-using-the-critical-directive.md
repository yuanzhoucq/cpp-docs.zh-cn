---
title: "A.5   Using the critical Directive | Microsoft Docs"
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
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.5   Using the critical Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例包含多个 `critical` 指令 \(在第 18 页\) 的[第2.6.2部分](../../parallel/openmp/2-6-2-critical-construct.md) 。  示例阐释任务取消并使用的一个队列模型。  若要防止取消同一任务的多个线程，取消排队的操作必须在 `critical` 部分。  由于本示例中的两个队列都是独立的，它们是使用其他名称、 *X 轴* 和 *Y 轴的*`critical` 指令保护。  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```