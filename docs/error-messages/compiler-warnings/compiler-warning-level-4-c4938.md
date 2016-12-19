---
title: "编译器警告（等级 4）C4938 | Microsoft Docs"
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
  - "C4938"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4938"
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4938
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：浮点型 reduction 变量可能会导致在 \/fp:strict 或 \#pragma fenv\_access 下出现不一致的结果  
  
 不应将 OpenMP 浮点型 reduction 变量与 [\/fp: strict](../../build/reference/fp-specify-floating-point-behavior.md) 或 [fenv\_access](../../preprocessor/fenv-access.md) 同时使用，因为求和计算的顺序不同。 因此，结果可能与不使用 \/openmp 的结果不同。  
  
 下面的示例生成 C4938：  
  
```  
// C4938.cpp // compile with: /openmp /W4 /fp:strict /c // #pragma fenv_access(on) extern double *a; double test(int first, int last) { double sum = 0.0; #pragma omp parallel for reduction(+: sum)   // C4938 for (int i = first ; i <= last ; ++i) sum += a[i]; return sum; }  
```  
  
 有显式并行化时，求和计算按如下方式进行：  
  
```  
sum = a[first] + a[first + 1] + ... + a[last];   
```  
  
 无显式并行化时，求和计算按如下方式进行：  
  
```  
sum1 = a[first] + ... a[first + last / 2]; sum2 = a[(first + last / 2) + 1] + ... a[last]; sum = sum1 + sum2;  
```