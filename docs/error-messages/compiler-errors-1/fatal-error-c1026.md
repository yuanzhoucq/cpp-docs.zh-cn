---
title: "错误 C1026 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1026"
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 错误 C1026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分析器堆栈溢出，程序太复杂  
  
 分析程序所需的空间导致编辑器堆栈溢出。  
  
 通过下列方法减少表达式的复杂性：  
  
-   减少 `for` 和 `switch` 语句中的嵌套。  将更深的嵌套语句放在单独的函数中。  
  
-   拆分涉及逗号运算符或函数调用的长表达式。