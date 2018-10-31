---
title: 3.3.1 omp_get_wtime 函数
ms.date: 11/04/2016
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
ms.openlocfilehash: 544a1bc9a613a2888cb7c5e68e54fdfae1b1c333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460562"
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