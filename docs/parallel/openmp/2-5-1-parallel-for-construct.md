---
title: 2.5.1 parallel for 构造
ms.date: 11/04/2016
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
ms.openlocfilehash: e74fa958a70fb10aadd39ccc6b4e56670bc072b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590324"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for 构造

**的并行**指令是一种快捷方式**并行**仅包含单个区域**为**指令。 语法**并行的**指令是按如下所示：

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

此指令允许的所有子句**并行**指令并**有关**指令，除`nowait`子句，使用相同的含义和限制。 语义是显式指定与相同**并行**指令后面紧跟**为**指令。

## <a name="cross-references"></a>交叉引用：

- **并行**指令，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。

- **有关**指令，请参阅[部分 2.4.1](../../parallel/openmp/2-4-1-for-construct.md)第 11 页上。

- 数据特性子句，请参阅[2.7.2 数据共享特性子句](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。