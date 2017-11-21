---
title: "4.4 OMP_NESTED |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb45bb04db612451c7d081f3a7afad8031da643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED`环境变量启用或禁用嵌套并行度，除非启用或禁用通过调用嵌套的并行`o` **mp_set_nested**库例程。 如果设置为**TRUE**，启用了嵌套并行机制; 如果设置为**FALSE**、 嵌套并行处于禁用状态。 默认值是**FALSE**。  
  
 示例:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>交叉引用：  
  
-   `omp_set_nested`函数中，请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上。