---
title: 3.1.8 omp_get_dynamic 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af7755173ab884a40a5f8a41f432f265cc1e6c32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函数
**Omp_get_dynamic**函数返回非零值，如果动态调整的线程已启用，且否则，返回 0。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 如果实现未实现动态调整的线程数，此函数将始终返回 0。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   有关动态线程调整的说明，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。