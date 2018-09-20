---
title: 3.1.8 omp_get_dynamic 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c30f49eaf91353d6a7cd9bd26e0e10e95cb6acd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426778"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函数

**Omp_get_dynamic**函数返回非零值，如果动态调整线程的已启用，否则返回 0。 格式如下所示：

```
#include <omp.h>
int omp_get_dynamic(void);
```

如果实现未实现动态调整线程数，此函数始终返回 0。

## <a name="cross-references"></a>交叉引用：

- 有关的动态线程调整说明，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。