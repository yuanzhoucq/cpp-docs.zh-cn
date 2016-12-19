---
title: "编译器错误 C3005 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3005"
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“error\_text”：OpenMP“directive”指令上出现意外的标记  
  
 OpenMP 指令格式不正确。  
  
 下面的示例生成 C3005：  
  
```  
// C3005.c // compile with: /openmp int main() { #pragma omp parallel + for   // C3005 }  
```  
  
 如果将左大括号放置在杂注所在的行，也会发生 C3005。  
  
```  
// C3005b.c // compile with: /openmp int main() { #pragma omp parallel {   // C3005 put open brace on next line lbl2:; } goto lbl2; }  
```