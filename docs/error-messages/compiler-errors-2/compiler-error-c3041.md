---
title: "编译器错误 C3041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3041"
ms.assetid: 9df1ae44-3ac7-4c6c-899f-f35ffe7ccf0d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：”copyprivate”子句中的变量在封闭上下文中必须是私有的  
  
 传递给 [copyprivate](../../parallel/openmp/reference/copyprivate.md) 的变量不能在封闭上下文中共享。  
  
 以下示例生成 C3041：  
  
```  
// C3041.cpp // compile with: /openmp /c #include "omp.h" double d; int main() { #pragma omp parallel shared(d) // try the following line instead // #pragma omp parallel private(d) { // or don't make d copyprivate #pragma omp single copyprivate(d)   // C3041 { } } }  
```