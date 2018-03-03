---
title: "A.27 利用 C99 可变长度数组 |Microsoft 文档"
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
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4bf3136c4fb4c5c14b728acbc61f3fbf66ce08bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27   使用 C99 变长数组
下面的示例演示如何使用 C99 变量长度数组 (VLAs) 中`firstprivate`指令 ([部分 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md)页 26 上)。  
  
> [!NOTE]
>  在 Visual c + + 中当前不支持可变长度数组。  
  
```  
void f(int m, int C[m][m])  
{  
    double v1[m];  
    ...  
    #pragma omp parallel firstprivate(C, v1)  
    ...  
}  
```