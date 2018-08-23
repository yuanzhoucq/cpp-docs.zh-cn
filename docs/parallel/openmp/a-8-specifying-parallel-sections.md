---
title: 指定并行部分 A.8 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acb28f4e7e99ea09696d116ab031778fcf9ff919
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694051"
---
# <a name="a8---specifying-parallel-sections"></a>A.8   指定并行段
在下面的示例中，(对于[部分 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)第 14 页上) 函数*xaxis*， *y 轴*，和*zaxis*可以并发执行。 第一个`section`指令是可选的。  请注意，所有`section`指令需要出现在词法范围内的`parallel sections`构造。  
  
```  
#pragma omp parallel sections  
{  
    #pragma omp section  
        xaxis();  
    #pragma omp section  
        yaxis();  
    #pragma omp section  
        zaxis();  
}  
```