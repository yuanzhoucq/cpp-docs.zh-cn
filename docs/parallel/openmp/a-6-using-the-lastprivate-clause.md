---
title: A.6   使用 lastprivate 子句
ms.date: 11/04/2016
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
ms.openlocfilehash: 7d5ba1413827590b7fb3afa0847b9aa1da3c41e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579798"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   使用 lastprivate 子句

有时正确的执行取决于循环的最后一次迭代将赋给变量的值。 此类程序必须列出所有此类变量作为参数`lastprivate`子句 ([部分 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md)页 27 上)，以便变量的值将与按顺序执行循环时相同。

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

在前面的示例中，值`i`末尾的并行区域将等于`n-1`，如下所示的顺序的情况。