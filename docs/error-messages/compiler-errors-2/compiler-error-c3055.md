---
title: "编译器错误 C3055 | Microsoft Docs"
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
  - "C3055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3055"
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”：符号在用于“threadprivate”指令之前无法引用  
  
 引用了一个符号，然后在 [threadprivate](../../parallel/openmp/reference/threadprivate.md) 子句中使用，这是不允许的。  
  
 下面的示例生成 C3055：  
  
```  
// C3055.cpp // compile with: /openmp int x, y; int z = x; #pragma omp threadprivate(x, y)   // C3055 void test() { #pragma omp parallel copyin(x, y) { x = y; } }  
```  
  
 可能的解决方法：  
  
```  
// C3055b.cpp // compile with: /openmp /LD int x, y, z; #pragma omp threadprivate(x, y) void test() { #pragma omp parallel copyin(x, y) { x = y; } }  
```