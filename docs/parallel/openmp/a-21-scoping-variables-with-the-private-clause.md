---
title: A.21   使用 private 子句设置变量范围
ms.date: 11/04/2016
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
ms.openlocfilehash: 4217bcc3911ded88b9385695c8c0ac851fceae9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616121"
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21   使用 private 子句设置变量范围

值`i`和`j`在以下示例中未定义在从并行区域退出：

```
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

有关详细信息`private`子句，请参阅[部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上。