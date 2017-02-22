---
title: "表达式计算器错误 CXX0030 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0030"
  - "CXX0030"
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 表达式计算器错误 CXX0030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表达式不可计算  
  
 调试器的表达式计算器未能获得所写的表达式的值。  可能的原因之一是该表达式引用了在程序地址空间以外的内存（取消引用空指针即属此例）。  Windows 不允许访问在程序地址空间以外的内存。  
  
 可能需要重写表达式，用圆括号控制计算顺序。  
  
 该错误与 CAN0030 相同。