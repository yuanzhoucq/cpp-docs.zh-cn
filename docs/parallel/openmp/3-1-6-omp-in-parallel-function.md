---
title: "3.1.6 omp_in_parallel 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e5d05af81eb112894ca27a7599c271138893ee1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函数
**Omp_in_parallel**如果调用在并行并行区域执行的动态范围内，函数将返回一个非零值; 否则，它将返回 0。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 此函数返回一个非零值时从内部并行，包括嵌套的区域序列化的区域执行调用。