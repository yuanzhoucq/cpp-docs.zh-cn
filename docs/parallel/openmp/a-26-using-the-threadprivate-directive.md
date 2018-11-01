---
title: A.26   使用 threadprivate 指令
ms.date: 11/04/2016
ms.assetid: 6eda76c2-c4f1-4208-a900-e0ea98a53eca
ms.openlocfilehash: 8ea810f8fbf8076b28464faafb72f5797d4a1a66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465424"
---
# <a name="a26---using-the-threadprivate-directive"></a>A.26   使用 threadprivate 指令

下面的示例演示如何使用`threadprivate`指令 ([部分 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) 23 页上) 为每个线程提供单独的计数器。

**示例 1:**

```
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

**示例 2:**

```
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```