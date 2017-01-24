---
title: "函数体 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "函数体"
  - "函数定义, 函数体"
  - "函数 [C], 语法"
  - "变量, 函数语法"
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函数体
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“函数体”是包含指定函数行为的语句的复合语句。  
  
## 语法  
 *function\-definition*:  
 *declaration\-specifiers*  opt *attribute\-seq* opt *declarator declaration\-list* opt *compound\-statement*  
  
 \/\* *attribute\-seq* 是 Microsoft 专用的 \*\/  
  
 *compound\-statement*: \/\* 函数体 \*\/  
 **{**  *declaration\-list*  opt *statement\-list* opt **}**  
  
 在函数体中声明的变量“局部变量”具有 **auto** 存储类，除非另行指定。  调用函数时，将为局部变量创建存储并执行本地初始化。  执行控制权将传递给 *compound\-statement* 中的第一个语句并继续传递，直到执行了 `return` 语句或到达函数体的末尾。  控制权随后返回到调用功能的点。  
  
 如果该函数返回了值，则必须执行包含表达式的 `return` 语句。  如果没有执行 `return` 语句或 `return` 语句不包含表达式，则函数的返回值是不确定的。  
  
## 请参阅  
 [C 函数定义](../c-language/c-function-definitions.md)