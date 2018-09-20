---
title: 4.1 OMP_SCHEDULE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbdad5ab56ea6979ae2b5952b092b5e85c7bdfa8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433447"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

**OMP_SCHEDULE**仅适用于**有关**并**为并行**具有计划类型的指令**运行时**。 通过向任何已识别的计划类型和一个可选设置此环境变量，可在运行时设置所有此类循环的计划类型和区块大小*使用 chunk_size*。

有关**为**和**的并行**而不具有计划类型的指令**运行时**， **OMP_SCHEDULE**将被忽略。 此环境变量的默认值是实现定义的。 如果可选*使用 chunk_size*值必须为正数的设置。 如果*使用 chunk_size*未设置，则假定此值为 1 的情况下除外**静态**计划。 有关**静态**计划，默认块区大小设置为循环迭代空间除以应用于循环的线程数。

示例:

```
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

## <a name="cross-references"></a>交叉引用：

- **有关**指令，请参阅[部分 2.4.1](../../parallel/openmp/2-4-1-for-construct.md)第 11 页上。

- **有关并行**指令，请参阅[部分 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)第 16 页上。