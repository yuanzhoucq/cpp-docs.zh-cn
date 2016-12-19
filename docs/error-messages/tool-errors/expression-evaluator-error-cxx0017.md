---
title: "表达式计算器错误 CXX0017 | Microsoft Docs"
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
  - "CXX0017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0017"
  - "CXX0017"
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未找到符号  
  
 未能找到表达式中指定的符号。  
  
 该错误可能的原因之一是符号名中大小写不匹配。  因为 C 和 C\+\+ 都是区分大小写的语言，所以必须完全按照源中定义的符号名大小写给定符号名。  
  
 尝试在调试期间为了监视变量而转换此变量的类型时可发生该错误。  `typedef` 声明类型的新名称，但不定义新类型。  在调试器中尝试进行的类型转换需要已定义类型名。  
  
 该错误与 CAN0017 相同。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  确保已在程序中将要使用该符号的地方声明了该符号。  
  
2.  使用实际类型名而不是 `typedef` 定义的名称来转换调试器中的变量类型。