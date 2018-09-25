---
title: A.27 使用 C99 变长数组 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51fda970f78592c8a4e10d17d370e9c78f0ea493
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405887"
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