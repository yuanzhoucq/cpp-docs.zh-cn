---
title: "表达式语句 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "表达式语句"
  - "语句, 表达式"
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 表达式语句
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表达式语句导致计算表达式。  出于表达式语句的原因，不会发生控制或迭代的传输。  
  
 表达式语句的语法就是  
  
## 语法  
  
```  
[expression ] ;  
```  
  
## 备注  
 在执行下一个语句前，将计算表达式语句中的所有表达式并完成所有副作用。  最常用的表达式语句是赋值和函数调用。由于表达式是可选的，因此单独的分号被视为空表达式语句，称为 [null](../cpp/null-statement.md) 语句。  
  
## 请参阅  
 [C\+\+ 语句概述](../cpp/overview-of-cpp-statements.md)