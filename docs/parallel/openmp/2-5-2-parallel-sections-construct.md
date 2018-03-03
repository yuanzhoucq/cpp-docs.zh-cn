---
title: "2.5.2 parallel sections 构造 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3a76a950d547effccf0b50fa04799814597bc5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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