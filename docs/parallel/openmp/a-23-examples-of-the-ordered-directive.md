---
title: A.23   ordered 指令的示例
ms.date: 11/04/2016
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
ms.openlocfilehash: 2868b771fd57613981f3c6458b48493a1b26eee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472268"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   ordered 指令的示例

可以有多个有序的部分`for`与指定`ordered`子句。 第一个示例是不符合要求，因为 API 指定以下：

"具有循环的迭代`for`构造必须执行相同`ordered`指令超过一次，并且它必须执行多个`ordered`指令。" (请参阅[部分 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) 22 页上)

在此不符合要求的示例中，所有迭代都执行有序的两个部分：

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

下面的示例符合`for`与多个有序部分：

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```