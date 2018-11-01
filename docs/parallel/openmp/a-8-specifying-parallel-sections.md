---
title: A.8   指定并行段
ms.date: 11/04/2016
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
ms.openlocfilehash: 81eaed920e77b23052ac58c2d0e18fee83c00565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461433"
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