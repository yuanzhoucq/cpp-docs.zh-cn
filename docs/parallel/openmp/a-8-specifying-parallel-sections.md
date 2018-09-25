---
title: A.8 指定并行段 |Microsoft Docs
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
ms.openlocfilehash: 9d969f1a0e9d9b282104ee00a3b2d06610533ad4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440415"
---
# <a name="a8---specifying-parallel-sections"></a>A.8   指定并行段

在以下示例中，(对于[部分 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)第 14 页上) 函数*xaxis*， *y 轴*，以及*zaxis*可以并发执行。 第一个`section`指令是可选的。  请注意，所有`section`指令需要出现在的词法范围`parallel sections`构造。

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