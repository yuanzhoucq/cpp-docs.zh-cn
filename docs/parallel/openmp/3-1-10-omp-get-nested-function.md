---
title: 3.1.10 omp_get_nested 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f447da6957cb385ace918120eb7ed7a5420e9f0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函数
`omp_get_nested`如果它处于禁用状态，函数将返回一个非零值，如果启用了嵌套并行机制和 0。 有关嵌套并行的详细信息，请参阅第页 40 页的部分 3.1.9。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 如果实现未实现嵌套并行度，则此函数始终返回 0。