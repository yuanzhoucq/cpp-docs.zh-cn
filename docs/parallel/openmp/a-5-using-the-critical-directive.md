---
title: "使用关键指令 A.5 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf4170fae6792906db29c90f61f067886b00f1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a5---using-the-critical-directive"></a>A.5   使用 critical 指令
下面的示例包括几个`critical`指令 ([部分 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 页上)。 该示例阐释了一个任务是取消排队和处理的队列模型。 若要防止出队相同的任务的多个线程，取消排队操作必须为`critical`部分。 由于在此示例中的两个队列都是独立的它们通过保护`critical`具有不同名称的指令*xaxis*和*y 轴*。  
  
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