---
title: 2.1 指令格式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eec5a2f0e91df6e8d71797199bd3a3911a3aab0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687266"
---
# <a name="21-directive-format"></a>2.1 指令格式
中的语法正式指定 OpenMP 指令的语法[附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)，和非正式的方式，如下所示：  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 每个指令开头 **#pragma omp**，来减少与其他 （非 OpenMP 或供应商扩展到 OpenMP） 杂注指令具有相同名称发生冲突的可能性。 指令的剩余部分遵循的编译器指令的 C 和 c + + 标准的约定。 之前和之后具体而言，可以使用空白**#**，并有时必须使用空格分隔词指令中的。 预处理标记后面 **#pragma omp**受到宏替换。  
  
 指令是区分大小写。 子句在指令中的显示顺序并不重要。 根据需要每个子句的说明中列出的限制的制约可能重复在指令上的子句。 如果*变量列表*将显示在子句中，它必须指定仅变量。 只有一个*指令名称*可以指定每个指令。  例如，不允许使用以下指令：  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP 指令适用于最多一个后续语句，它必须是结构化的块中。