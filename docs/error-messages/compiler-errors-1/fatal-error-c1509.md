---
title: "错误 C1509 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1509"
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

1234.5678 \("\#\#\#\#\#"\) \-1235编译器限制 : 函数“function”中有太多异常处理程序状态。简化函数  
  
代码超过异常处理程序状态的内部限制（32,768 个状态）。  
  
最常见的子句是包含用户定义的类变量和算术运算符的复杂表达式的函数。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  将普通的子表达式分配到临时变量以简化表达式。  
  
2.  将函数拆分为更小的函数。