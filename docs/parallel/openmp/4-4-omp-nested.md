---
title: 4.4 OMP_NESTED
ms.date: 11/04/2016
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
ms.openlocfilehash: e45b8901c56923ab37ca387a5f057c5b41af21f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453610"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED`环境变量启用或禁用嵌套并行度，除非启用或禁用通过调用嵌套并行度`o` **mp_set_nested**库例程。 如果设置为 **，则返回 TRUE**，启用了嵌套并行机制; 如果设置为**FALSE**、 嵌套禁用并行度。 默认值是**FALSE**。

示例:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>交叉引用：

- `omp_set_nested` 函数中，请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上。