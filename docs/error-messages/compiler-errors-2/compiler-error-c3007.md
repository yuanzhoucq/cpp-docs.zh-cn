---
title: "编译器错误 C3007 | Microsoft Docs"
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
  - "C3007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3007"
ms.assetid: e415ef42-bdc9-4f32-8198-5e25b289a089
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“arg”: OpenMP“directive”指令上的子句没有采用参数  
  
 OpenMP 指令具有一个参数，但没有采用参数。  
  
 以下示例生成 C3007：  
  
```  
// C3007.c // compile with: /openmp int main() { #pragma omp parallel for ordered(2)   // C3007 }  
```