---
title: "编译器错误 C2410 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2410"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2410"
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2410
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”:“context”中不明确的成员名称  
  
 该标识符是此上下文中多个结构或联合的成员。  
  
 请对导致该错误的操作数使用结构或联合说明符。  结构或联合说明符是类型 `struct` 或 `union` 的标识符（`typedef` 名称或与所引用的结构或联合的类型相同的变量）。  该说明符必须是要使用该操作数的第一个成员选择运算符 \(.\) 左边的操作数。