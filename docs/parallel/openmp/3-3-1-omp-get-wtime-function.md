---
title: 3.3.1 omp_get_wtime 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec022e9c7e27c848ef535481993dd18dc45f695
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430758"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime 函数

`omp_get_wtime`函数将返回在过去某个"时间"以来的秒的已用的挂钟时间双精度浮点值。  实际"过去的时间"是任意的但它肯定不在应用程序的执行期间更改。 格式如下所示：

```
#include <omp.h>
double omp_get_wtime(void);
```

我们已预见该函数将用于测量运行时间，如下面的示例中所示：

```
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返回的时间的"每个线程时间"这意味着他们不需要是全局一致参与应用程序中的所有线程。