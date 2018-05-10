---
title: 有序指令 A.23 示例 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37cc4ea9db8cbd1a7bf095e2bde0ae482053a584
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   ordered 指令的示例
可以具有多个有序的部分`for`指定`ordered`子句。 第一个示例是不符合要求，因为指定以下 API:  
  
 "具有循环的迭代`for`构造不能执行相同`ordered`指令超过一次，而且它不能执行多个`ordered`指令。" (请参阅[部分 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md)在页上 22)  
  
 在此不符合要求的示例中，所有迭代都执行有序的两个部分：  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 以下符合示例所示`for`与多个经过排序的节：  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```