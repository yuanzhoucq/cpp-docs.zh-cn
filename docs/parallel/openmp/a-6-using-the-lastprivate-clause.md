---
title: A.6 使用 lastprivate 子句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d18d3aaf5c5d1cbe03282710ae4f4e2bb613f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390573"
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