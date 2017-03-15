---
title: "表达式计算器错误 CXX0025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0025"
  - "CXX0025"
ms.assetid: 3e2fb541-63b3-46ac-9f93-3dadb253bcf6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 表达式计算器错误 CXX0025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

运算符要求结构\/联合  
  
 采用 `struct` 或 **union** 类型表达式的运算符应用到非 `struct` 或 **union** 的表达式。  
  
 类、结构或联合变量的组成部分必须具有完全限定名。  不能在没有完全规范的情况下输入组成部分。  
  
 该错误与 CAN0025 相同。