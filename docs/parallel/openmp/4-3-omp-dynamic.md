---
title: 4.3 OMP_DYNAMIC |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c15fa9d8c9d86b736bfc577a3b17e9809ec9baaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439193"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

**OMP_DYNAMIC**环境变量启用或禁用动态调整可用的并行区域执行的线程数，除非显式启用或禁用通过调用动态调整**omp_set_dynamic**库例程。 其值必须是 **，则返回 TRUE**或**FALSE**。

如果设置为 **，则返回 TRUE**，可能由运行时环境来充分地利用系统资源调整用于执行并行区域的线程数。  如果设置为**FALSE**，禁用动态调整。 默认条件是实现定义的。

示例:

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>交叉引用：

- 并行区域的详细信息，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。

- **omp_set_dynamic**函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。