---
title: 3.1.4 omp_get_thread_num 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a21a682c051daffde16b3d5cfc63fd2d679c4de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444913"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 函数

`omp_get_thread_num`函数将返回线程数，其团队中执行该函数的线程。 线程数作用在于它介于 0 和**omp_get_num_threads()**-1，非独占。 团队的主线程是线程 0。

格式如下所示：

```
#include <omp.h>
int omp_get_thread_num(void);
```

如果从串行区域中，调用`omp_get_thread_num`返回 0。 如果从调用序列化嵌套并行区域内，此函数将返回 0。

## <a name="cross-references"></a>交叉引用：

- `omp_get_num_threads` 函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 页上。