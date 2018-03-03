---
title: "2.1 指令格式 |Microsoft 文档"
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
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3ff4e0078ffd086ce3b62d8927184188f0ebdd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="21-directive-format"></a>2.1 指令格式
中的语法正式指定 OpenMP 指令的语法[附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)，和非正式的方式，如下所示：  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 每个指令开头**#pragma omp**，来减少与其他 （非 OpenMP 或供应商扩展到 OpenMP） 杂注指令具有相同名称发生冲突的可能性。 指令的剩余部分遵循的编译器指令的 C 和 c + + 标准的约定。 之前和之后具体而言，可以使用空白 **#** ，并有时必须使用空格分隔词指令中的。 预处理标记后面**#pragma omp**受到宏替换。  
  
 指令是区分大小写。 子句在指令中的显示顺序并不重要。 根据需要每个子句的说明中列出的限制的制约可能重复在指令上的子句。 如果*变量列表*将显示在子句中，它必须指定仅变量。 只有一个*指令名称*可以指定每个指令。  例如，不允许使用以下指令：  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP 指令适用于最多一个后续语句，它必须是结构化的块中。