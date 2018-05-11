---
title: 2.5.1 parallel for 构造 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2732c4f8713466d282346ea240bd3c41886ce0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for 构造
**为并行**指令是的快捷方式**并行**区域包含单个仅**为**指令。 语法**为并行**指令是，如下所示：  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop  
```  
  
 此指令允许的所有子句**并行**指令和**为**指令，除`nowait`子句，使用相同的含义和限制。 语义相等显式指定**并行**指令紧跟**为**指令。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **并行**指令，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。  
  
-   **有关**指令，请参阅[部分 2.4.1](../../parallel/openmp/2-4-1-for-construct.md)第 11 页上。  
  
-   数据特性子句，请参阅[2.7.2 数据共享特性子句](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)第 25 页上。