---
title: A.1 并行执行简单的循环 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5446f72cc5ee0577385527be24bc912297aec0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418939"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   并行执行简单循环

下面的示例演示如何以并行执行简单的循环使用`parallel for`指令 ([部分 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)第 16 页上)。 循环迭代变量是默认情况下，专用的因此不需要专用的子句中显式指定它。

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```