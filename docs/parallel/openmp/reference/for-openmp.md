---
title: 对于 (OpenMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- for
dev_langs:
- C++
helpviewer_keywords:
- for OpenMP directive
ms.assetid: 8b54e034-9db2-4c1a-a2b1-72e14e930506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fea7679e8e2d27db8f8f4ff4087bae6ebc84ab1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439544"
---
# <a name="for-openmp"></a>for (OpenMP)

导致中完成的工作有关要在线程之间划分的并行区域内的循环。

## <a name="syntax"></a>语法

```
#pragma omp [parallel] for [clauses]
   for_statement
```

## <a name="arguments"></a>自变量

*子句*<br/>
（可选）零个或多个子句。 请参阅支持的子句的列表的备注部分**为**。

*for_statement*<br/>
一个 for 循环。 如果用户代码中，将会导致未定义的行为的循环更改索引变量。

## <a name="remarks"></a>备注

**为**指令支持以下 OpenMP 子句：

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)

- [lastprivate](../../../parallel/openmp/reference/lastprivate.md)

- [nowait](../../../parallel/openmp/reference/nowait.md)

- [排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)

- [private](../../../parallel/openmp/reference/private-openmp.md)

- [reduction](../../../parallel/openmp/reference/reduction.md)

- [schedule](../../../parallel/openmp/reference/schedule.md)

如果**并行**同时指定，则`clause`可以会被接受的任何子句**并行**或**有关**指令，除**nowait**.

有关详细信息，请参阅[2.4.1 for 构造](../../../parallel/openmp/2-4-1-for-construct.md)。

## <a name="example"></a>示例

```
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="see-also"></a>请参阅

[指令](../../../parallel/openmp/reference/openmp-directives.md)