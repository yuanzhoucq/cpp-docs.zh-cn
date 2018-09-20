---
title: omp_get_num_procs |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_num_procs
dev_langs:
- C++
helpviewer_keywords:
- omp_get_num_procs OpenMP function
ms.assetid: 14a10b8f-e59b-4211-a292-687648c9f760
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74e4d224f28721e3849350e8f12010078edba4a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437373"
---
# <a name="ompgetnumprocs"></a>omp_get_num_procs

返回调用函数时可用的处理器数。

## <a name="syntax"></a>语法

```
int omp_get_num_procs();
```

## <a name="remarks"></a>备注

有关详细信息，请参阅[3.1.5 omp_get_num_procs 函数](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)。

## <a name="example"></a>示例

```
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="see-also"></a>请参阅

[函数](../../../parallel/openmp/reference/openmp-functions.md)