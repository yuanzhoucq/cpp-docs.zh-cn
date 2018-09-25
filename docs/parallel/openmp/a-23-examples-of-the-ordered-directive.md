---
title: A.23 ordered 指令的示例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec609a77e9bdc7cbdbb0822dfde0a88110ce0244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405965"
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