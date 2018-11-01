---
title: 3.1.6 omp_in_parallel 函数
ms.date: 11/04/2016
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
ms.openlocfilehash: 2f251cb994771278c7f4e3f50f01e02126f6f88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482038"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函数

**Omp_in_parallel**如果并行并行区域执行的动态范围内被调用的函数将返回一个非零值; 否则，它将返回 0。 格式如下所示：

```
#include <omp.h>
int omp_in_parallel(void);
```

此函数返回一个非零值时从区域并行执行，其中包括被序列化的嵌套的区域内调用。