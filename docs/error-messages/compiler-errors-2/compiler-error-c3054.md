---
title: "编译器错误 C3054 | Microsoft Docs"
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
  - "C3054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3054"
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当前在泛型类或函数中不支持“\#pragma omp parallel”  
  
 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)和[OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C3054。  
  
```  
// C3054.cpp // compile with: /openmp /clr /c #include <omp.h> ref struct MyBaseClass { // Delete the following 7 lines to resolve. generic <class ItemType> void Test(ItemType i) {   // C3054 #pragma omp parallel num_threads(4) { int i = omp_get_thread_num(); } } // OK void Test2() { #pragma omp parallel num_threads(4) { int i = omp_get_thread_num(); } } };  
```