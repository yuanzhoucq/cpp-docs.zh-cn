---
title: A.27   使用 C99 变长数组
ms.date: 11/04/2016
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
ms.openlocfilehash: 7b2ee74dcd5adedd02e7a9b311c5d3f67203d892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655294"
---
# <a name="a27---use-of-c99-variable-length-arrays"></a>A.27   使用 C99 变长数组

下面的示例演示如何使用 C99 变量长度数组 (VLAs) 中`firstprivate`指令 ([部分 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md)第 26 页上)。

> [!NOTE]
>  在 Visual c + + 中当前不支持可变长度数组。

```
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```