---
title: "使用 reduction 子句 A.7 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e71e65bc-a25c-4f02-b507-66b52bf950a4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 478bc91126e207b79800db85023925a9430bd0cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a7---using-the-reduction-clause"></a>A.7   使用 reduction 子句
下面的示例演示 reduction 子句 ([部分 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md)页 28 上):  
  
```  
#pragma omp parallel for private(i) shared(x, y, n) \  
                         reduction(+: a, b)  
    for (i=0; i<n; i++) {  
        a = a + x[i];  
        b = b + y[i];  
    }  
```