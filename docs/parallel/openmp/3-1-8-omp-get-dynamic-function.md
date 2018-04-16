---
title: "3.1.8 omp_get_dynamic 函数 |Microsoft 文档"
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
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd4ec73b82848efcdface781738639b05a256958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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