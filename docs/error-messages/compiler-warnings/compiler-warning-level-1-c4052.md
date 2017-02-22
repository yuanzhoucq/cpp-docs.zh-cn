---
title: "编译器警告（等级 1）C4052 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4052"
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数声明不同；一个包含变量参数  
  
 函数的一个声明不包含变量参数。 它将被忽略。  
  
 以下示例生成 C4052：  
  
```  
// C4052.c // compile with: /W4 /c int f(); int f(int i, ...);   // C4052  
```