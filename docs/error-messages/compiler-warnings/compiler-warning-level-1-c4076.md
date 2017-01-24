---
title: "编译器警告（等级 1）C4076 | Microsoft Docs"
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
  - "C4076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4076"
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“typemod”: 不能和“typename”类型一起使用  
  
 类型修饰符（无论是**有符号**还是 `unsigned`）不能用于非整数类型。***typemod*** 将被忽略。  
  
## 示例  
 以下示例生成 C4076:  
  
```  
// C4076.cpp // compile with: /W1 /LD unsigned double x;   // C4076  
```