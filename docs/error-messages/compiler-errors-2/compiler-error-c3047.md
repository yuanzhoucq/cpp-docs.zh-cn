---
title: "编译器错误 C3047 | Microsoft Docs"
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
  - "C3047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3047"
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP“sections”区域中的结构化块的前面必须是“\#pragma omp section”  
  
 [sections](../../parallel/openmp/reference/sections-openmp.md) 指令所引入代码块中的任何代码必须位于 `section` 指令引入的代码块中。  
  
 下面的示例生成 C3047：  
  
```  
// C3047.cpp // compile with: /openmp /c #include "omp.h" int main() { int n2 = 2, n3 = 3; #pragma omp parallel { ++n2; #pragma omp sections { #pragma omp section { ++n3; } ++n2;   // C3047 not enclosed in #pragma omp section } } }  
```