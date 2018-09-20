---
title: 2.2 条件编译 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25b52ce624777efe85e27b8ce5e7941bc2f5dcba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440376"
---
# <a name="22-conditional-compilation"></a>2.2 条件编译

_**OPENMP**宏名称指由符合 OpenMP 的实现的十进制常数*yyyymm*，它将是年份和月份的已批准的规范。 此宏的使用者不能 **#define**或 **#undef**预处理指令。

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果供应商定义扩展，OpenMP，他们可以指定其他预定义的宏。