---
title: 4.4 OMP_NESTED |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1779b75774a2177a0d6a4f0661406e28b479a7ee
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690265"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED`环境变量启用或禁用嵌套并行度，除非启用或禁用通过调用嵌套的并行`o` **mp_set_nested**库例程。 如果设置为**TRUE**，启用了嵌套并行机制; 如果设置为**FALSE**、 嵌套并行处于禁用状态。 默认值是**FALSE**。  
  
 示例:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>交叉引用：  
  
-   `omp_set_nested` 函数中，请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上。