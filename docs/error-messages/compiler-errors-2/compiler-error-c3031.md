---
title: "编译器错误 C3031 | Microsoft Docs"
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
  - "C3031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3031"
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：“reduction”子句中的变量必须是标量算术类型  
  
 向 reduction 子句传递了错误类型的变量。  
  
 下面的示例生成 C3031：  
  
```  
// C3031.cpp // compile with: /openmp /link vcomps.lib #include <stdio.h> #include "omp.h" typedef struct { int n; } Incomplete; extern Incomplete inc; int i = 9; int main() { #pragma omp parallel reduction(+: inc)   // C3031 ; #pragma omp parallel reduction(+: i)     // OK ; }  
```