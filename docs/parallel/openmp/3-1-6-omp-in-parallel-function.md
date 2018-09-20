---
title: 3.1.6 omp_in_parallel 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ba6c35d42f8497869894bd5ec95b83f0c8793f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404613"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函数

**Omp_in_parallel**如果并行并行区域执行的动态范围内被调用的函数将返回一个非零值; 否则，它将返回 0。 格式如下所示：

```
#include <omp.h>
int omp_in_parallel(void);
```

此函数返回一个非零值时从区域并行执行，其中包括被序列化的嵌套的区域内调用。