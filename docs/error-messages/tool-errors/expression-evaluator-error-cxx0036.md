---
title: "表达式计算器错误 CXX0036 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0036"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0036"
  - "CXX0036"
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 表达式计算器错误 CXX0036
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

错误的上下文 {...} 规范  
  
 此消息可由上下文运算符 \(**{}**\) 用法错误中的任何一个错误生成。  
  
-   未正确给定上下文运算符 \(**{}**\) 的语法。  
  
     上下文运算符的语法是：  
  
     {*function*,*module*,*dll*}*expression*  
  
     该语法指定了 *expression* 的上下文。  该上下文运算符具有与类型转换相同的优先级和用法。  
  
     可以省略后面的逗号。  如果 *function*、*module* 或 *dll* 中的任何一个包含逗号，则必须用圆括号将整个名称括起来。  
  
-   该函数名拼写不正确，或者在指定模块或动态链接库中不存在。  
  
     因为 C 是区分大小写的语言，所以 *function* 必须完全按照它在源中定义的大小写给定。  
  
-   未能找到此模块或 DLL。  
  
     检查指定模块或 DLL 的全路径名。  
  
 该错误与 CAN0036 相同。