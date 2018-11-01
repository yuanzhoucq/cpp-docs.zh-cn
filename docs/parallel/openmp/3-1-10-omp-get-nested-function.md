---
title: 3.1.10 omp_get_nested 函数
ms.date: 11/04/2016
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
ms.openlocfilehash: a4db1e21f344f5cc58e2027b0816f9c8fb40b3bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519903"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函数

`omp_get_nested`函数返回一个非零值，如果启用了嵌套并行机制和 0，如果它处于禁用状态。 嵌套的并行度的详细信息，请参阅 40 页上的部分 3.1.9。 格式如下所示：

```
#include <omp.h>
int omp_get_nested(void);
```

如果实现未实现嵌套并行度，则此函数始终返回 0。