---
title: 2.5.2 parallel sections 构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 073d0561fe4bfbb96ed88681a077da6fc985c963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402325"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections 构造

**并行部分**指令提供用于指定快捷窗体**并行**包含只有一个区域**部分**指令。 语义是显式指定与相同**并行**指令后面紧跟**部分**指令。 语法**并行部分**指令是按如下所示：

```
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是一个接受的子句**并行**并**部分**指令，除**nowait**子句。

## <a name="cross-references"></a>交叉引用：

- **并行**指令，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。

- **部分**指令，请参阅[部分 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)第 14 页上。