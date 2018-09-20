---
title: 如果 (OpenMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4aaad878040534fd198bcdf4a93d7820fd89adc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404808"
---
# <a name="if-openmp"></a>if (OpenMP)

指定并行或序列中是否应执行一个循环。

## <a name="syntax"></a>语法

```
if(expression)
```

### <a name="parameters"></a>参数

*表达式*<br/>
整数表达式，如果其计算结果为 true （非零），将导致并行区域以并行执行的代码。 如果表达式的计算结果为 false （零），并行区域是在序列中执行 （由单线程）。

## <a name="remarks"></a>备注

`if` 适用于以下指令：

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [部分](../../../parallel/openmp/reference/sections-openmp.md)

有关详细信息，请参阅[2.3 parallel 构造](../../../parallel/openmp/2-3-parallel-construct.md)。

## <a name="example"></a>示例

```
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="see-also"></a>请参阅

[子句](../../../parallel/openmp/reference/openmp-clauses.md)