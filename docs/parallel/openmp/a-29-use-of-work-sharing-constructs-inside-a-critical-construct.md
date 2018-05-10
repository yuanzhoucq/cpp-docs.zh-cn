---
title: A.29 使用的工作共享构造内 critical 构造 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccbb39a9067adf545339d02fe0c05e24fbcdb0a4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29   critical 构造内工作共享构造的使用
下面的示例演示如何使用内部的工作共享构造`critical`构造。 此示例是符合的因为工作共享构造和`critical`构造未将绑定到同一并行区域。  
  
```  
void f()  
{  
  int i = 1;  
  #pragma omp parallel sections  
  {  
    #pragma omp section  
    {  
      #pragma omp critical (name)  
      {  
        #pragma omp parallel  
        {  
          #pragma omp single  
          {  
            i++;  
          }  
        }  
      }  
    }  
  }  
}  
```