---
title: "后缀运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运算符 [C], 后缀"
  - "后缀运算符"
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 后缀运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

后缀运算符在表达式计算中具有最高优先级（最紧密的绑定）。  
  
## 语法  
 *postfix\-expression*:  
 *primary\-expression*  
  
 *postfix\-expression*  **\[**  *expression*  **\]**  
  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *postfix\-expression*  **.**  *identifier*  
  
 *postfix\-expression*  **–\>**  *identifier*  
  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 具有此优先级别的运算符为数组下标、函数调用、结构和联合成员以及后缀递增和递减运算符。  
  
## 请参阅  
 [C 运算符](../c-language/c-operators.md)