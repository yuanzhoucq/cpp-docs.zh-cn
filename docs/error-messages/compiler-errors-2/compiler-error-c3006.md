---
title: "编译器错误 C3006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3006"
ms.assetid: 449082ec-fd45-4c47-8ab3-ba6a719e4dc4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“clause”：OpenMP“directive”指令上的子句缺少应有的参数  
  
 OpenMP 指令没有应有的参数。  
  
 下面的示例生成 C3006：  
  
```  
// C3006.c // compile with: /openmp int main() { #pragma omp parallel shared   // C3006 // Try the following line instead: // #pragma omp parallel shared(x) {} }  
```