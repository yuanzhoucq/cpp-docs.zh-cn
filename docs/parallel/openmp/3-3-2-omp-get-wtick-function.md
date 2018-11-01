---
title: 3.3.2 omp_get_wtick 函数
ms.date: 11/04/2016
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
ms.openlocfilehash: af1e5cf8ef40621342a5162f90cf8c883a59c6a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617953"
---
# <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 函数

`omp_get_wtick`函数将返回连续的时钟计时周期之间等待的秒数双精度浮点值。 格式如下所示：

```
#include <omp.h>
double omp_get_wtick(void);
```