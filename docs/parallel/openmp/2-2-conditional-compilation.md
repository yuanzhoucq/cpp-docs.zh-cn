---
title: 2.2 条件编译
ms.date: 11/04/2016
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
ms.openlocfilehash: 9dc107ee9e5328df205d4b6f826f71c23abfb3ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658544"
---
# <a name="22-conditional-compilation"></a>2.2 条件编译

_**OPENMP**宏名称指由符合 OpenMP 的实现的十进制常数*yyyymm*，它将是年份和月份的已批准的规范。 此宏的使用者不能 **#define**或 **#undef**预处理指令。

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果供应商定义扩展，OpenMP，他们可以指定其他预定义的宏。