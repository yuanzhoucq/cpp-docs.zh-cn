---
title: "2.5.1 parallel for 构造 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7dcd763b68a78e11c3c33bf3d750a26e88ad02ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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