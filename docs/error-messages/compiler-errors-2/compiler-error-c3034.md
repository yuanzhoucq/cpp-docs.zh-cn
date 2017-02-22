---
title: "编译器错误 C3034 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3034"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3034"
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3034
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP“directive1”指令不能直接嵌套在“directive2”指令中  
  
 一些指令不能嵌套。 若要修复此错误，你可以将这两个指令语句合并到一个指令的块中或可以构造连续指令。  
  
 以下示例生成 C3034：  
  
```  
// C3034.cpp // compile with: /openmp /link vcomps.lib int main() { #pragma omp single { #pragma omp single   // C3034 { ; } } // Two consecutive single clauses are OK. #pragma omp single { } #pragma omp single { } }  
```