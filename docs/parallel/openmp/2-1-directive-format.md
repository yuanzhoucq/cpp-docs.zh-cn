---
title: "2.1 Directive Format | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.1 Directive Format
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP 指令的语法由 [附录 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)于以下语法形式指定和非正式地:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 每个指令从 **\#pragma omp**开始，减少发生冲突的风险与同名的其他 \(对 OpenMP 的非 OpenMP 或供应商扩展\) 杂注指令。  指令的其余部分遵循 C 和 C\+\+ 标准约定编译器指令的。  特别是，在 **\#**前后，空白可以使用，并且，有时必须使用空格分隔指令中的单词。  按照 **\#pragma omp** 的预处理标记受宏替换。  
  
 指令区分大小写。  子句出现在指令的顺序并不重要。  指令中的子句能重复根据需要，这取决于列表的限制在每个子句的说明。  如果 *将变量列表* 显示在子句，它必须只指定变量。  仅指令 *名称* 可以每条指令以指定。  例如，下面的指令不允许:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP 指令适用于最多一个成功的语句，必须是构造的块。