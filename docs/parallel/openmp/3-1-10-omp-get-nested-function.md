---
title: 3.1.10 omp_get_nested 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d019dd757080bbc87ff7aaab1a8745b2a3156b39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392269"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函数

`omp_get_nested`函数返回一个非零值，如果启用了嵌套并行机制和 0，如果它处于禁用状态。 嵌套的并行度的详细信息，请参阅 40 页上的部分 3.1.9。 格式如下所示：

```
#include <omp.h>
int omp_get_nested(void);
```

如果实现未实现嵌套并行度，则此函数始终返回 0。