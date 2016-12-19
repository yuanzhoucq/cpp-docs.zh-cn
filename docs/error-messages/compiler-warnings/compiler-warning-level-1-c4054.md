---
title: "编译器警告（等级 1）C4054 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4054"
ms.assetid: bdd7f6d5-f6f2-44a7-a013-39f309de7a29
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“conversion”：从函数指针“type1”到数据指针“type2”  
  
 函数指针被强制（可能是错误地）转换为数据指针。 这是 \/Za 下的 1 级警告和 \/Ze 下的 4 级警告。  
  
 下面的示例生成 C4054：  
  
```  
// C4054.c // compile with: /W1 /Za /c int (*pfunc)(); int* f() { return (int*)pfunc;   // C4054 }  
```  
  
 在 \/Ze 下，这是 4 级警告。  
  
```  
// C4054b.c // compile with: /W4 /c int (*pfunc)(); int* f() { return (int*)pfunc;   // C4054 }  
```