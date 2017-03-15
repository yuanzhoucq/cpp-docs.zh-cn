---
title: "编译器错误 C3012 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3012"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3012"
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3012
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“intrinsic”: 并行区域内不允许直接使用内部函数  
  
 `omp`  `parallel` 区域内不允许使用[编译器内部函数](../../intrinsics/compiler-intrinsics.md)。  
  
 下面的示例生成 C3012：  
  
```  
// C3012.cpp // compile with: /openmp #ifdef __cplusplus extern "C" { #endif void* _ReturnAddress(); #ifdef __cplusplus } #endif int main() { _ReturnAddress();   // OK #pragma omp parallel { _ReturnAddress();   // C3012 } }  
```