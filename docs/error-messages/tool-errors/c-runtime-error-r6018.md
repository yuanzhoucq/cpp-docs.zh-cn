---
title: "C 运行时错误 R6018 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6018"
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C 运行时错误 R6018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的堆错误  
  
 程序在执行内存管理操作时遇到意外错误。  
  
 如果程序不小心改变了运行时堆数据，通常会发生该错误。  但该错误也可由运行时或操作系统代码中的内部错误引起。  
  
 如果您的编译器可提供包含 `_heapchk` 和 `_heapwalk` 的库，则您可使用这些函数诊断该错误。