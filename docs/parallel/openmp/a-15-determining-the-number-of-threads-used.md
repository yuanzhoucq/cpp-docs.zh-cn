---
title: A.15 确定使用的线程数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1042b4871f53bddb5cff894330f3afe7d8a088ef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428730"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   确定使用的线程数

请考虑以下不正确的示例 (对于[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 页上):

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()`串行节的代码，因此调用返回 1 *np*始终将等于 1 在前面的示例。 若要确定将为并行区域部署的线程数，请调用应并行区域内。

下面的示例演示如何重写此程序，而不包含查询的线程数：

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```