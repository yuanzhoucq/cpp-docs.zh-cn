---
title: 2.5.2 parallel sections 构造 |Microsoft 文档
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
ms.openlocfilehash: b6f7a84e322cb273733c6a724ee2563928df8362
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689475"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections 构造
**并行部分**指令提供快捷窗体，用于指定**并行**区域包含只有一个**部分**指令。 语义相等显式指定**并行**指令紧跟**部分**指令。 语法**并行部分**指令是，如下所示：  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block  ]  
   ...  
}  
```  
  
 *子句*可以是接受的子句之一**并行**和**部分**指令，除**nowait**子句。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **并行**指令，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。  
  
-   **部分**指令，请参阅[部分 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)第 14 页上。