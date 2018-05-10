---
title: 3.1.6 omp_in_parallel 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22b491695d2ae49336d7d8998af64e724f344d87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函数
**Omp_in_parallel**如果调用在并行并行区域执行的动态范围内，函数将返回一个非零值; 否则，它将返回 0。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 此函数返回一个非零值时从内部并行，包括嵌套的区域序列化的区域执行调用。