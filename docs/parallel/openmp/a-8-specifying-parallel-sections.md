---
title: "指定并行部分 A.8 |Microsoft 文档"
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
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db7decc4efb1a3f6bb457623489c84e0ad1ae1f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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