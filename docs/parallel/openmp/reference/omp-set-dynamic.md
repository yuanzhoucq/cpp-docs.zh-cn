---
title: omp_set_dynamic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6032503f0b9ccb7d3492f1337165c9db7ec2113a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373904"
---
# <a name="ompsetdynamic"></a>omp_set_dynamic

指示运行时可进行调整的后续并行区域中可用的线程数。

## <a name="syntax"></a>语法

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>参数

*val*<br/>
一个值，指示是否可以通过在运行时调整后续并行区域中可用的线程数。  如果非零，则运行时可以调整的线程数，如果为零，则运行时将不会动态调整线程数。

## <a name="remarks"></a>备注

线程数将永远不会超出设置的值[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或通过[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)。

使用[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)若要显示的当前设置`omp_set_dynamic`。

设置`omp_set_dynamic`将覆盖的设置[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)环境变量。

有关详细信息，请参阅[3.1.7 omp_set_dynamic 函数](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

## <a name="example"></a>示例

```
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="see-also"></a>请参阅

[函数](../../../parallel/openmp/reference/openmp-functions.md)