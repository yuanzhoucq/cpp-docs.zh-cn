---
title: "编译器警告（等级 1）C4055 | Microsoft Docs"
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
  - "C4055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4055"
ms.assetid: f04b13ca-88a7-4f2b-8065-42e73e5ac353
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“conversion”：从数据指针“type1”到函数指针“type2”  
  
 数据指针被（可能是错误地）强制转换为函数指针。 这是 \/Za 下的 1 级警告和 \/Ze 下的 4 级警告。  
  
 以下示例生成 C4055：  
  
```  
// C4055.c // compile with: /Za /W1 /c typedef int (*PFUNC)(); int *pi; PFUNC f() { return (PFUNC)pi;   // C4055 }  
```  
  
 在 \/Ze 下，这是 4 级警告。  
  
```  
// C4055b.c // compile with: /W4 /c typedef int (*PFUNC)(); int *pi; PFUNC f() { return (PFUNC)pi;   // C4055 }  
```