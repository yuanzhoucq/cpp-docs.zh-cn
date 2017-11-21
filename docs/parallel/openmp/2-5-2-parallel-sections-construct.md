---
title: "2.5.2 parallel sections 构造 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 086552c72e37822920e0afa213c7966befa052f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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