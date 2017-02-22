---
title: "lastprivate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "lastprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lastprivate OpenMP clause"
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# lastprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定变量的封闭上下文的版本使用专用版本将被设置为等于线程执行最终迭代 \(对于循环构造\) 或前一节 \(\#pragma 节\)。  
  
## 语法  
  
```  
lastprivate(var)  
```  
  
## 备注  
 其中，  
  
 `var`  
 设置为等于专用版本的变量线程执行最终迭代 \(对于循环构造\) 或前一节 \(\#pragma 节\)。  
  
## 备注  
 `lastprivate` 适用于以下指令:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关更多信息，请参见 [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。  
  
## 示例  
 有关使用示例 `lastprivate` 子句参见 [schedule](../../../parallel/openmp/reference/schedule.md) 。  
  
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)