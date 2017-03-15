---
title: "barrier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "barrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "barrier OpenMP directive"
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# barrier
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

同步团队的所有线程;所有线程暂停在关卡，，直到所有线程执行关卡。  
  
## 语法  
  
```  
#pragma omp barrier  
```  
  
## 备注  
 `barrier` 指令不支持 OpenMP 子句。  
  
 有关更多信息，请参见 [2.6.3 barrier Directive](../../../parallel/openmp/2-6-3-barrier-directive.md)。  
  
## 示例  
 有关此示例演示如何使用 `barrier`，请参见 [master](../../../parallel/openmp/reference/master.md)。  
  
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)