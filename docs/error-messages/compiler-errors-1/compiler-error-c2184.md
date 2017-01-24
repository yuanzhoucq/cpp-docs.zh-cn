---
title: "编译器错误 C2184 | Microsoft Docs"
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
  - "C2184"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2184"
ms.assetid: 80fc8bff-7d76-4bde-94d2-01d84bb6824a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2184
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：对 \_\_except 表达式而言为非法类型，必须为整型  
  
 [\_\_except](../../c-language/try-except-statement-c.md) 语句中使用了某个类型，但不允许使用该类型。  
  
 下面的示例生成 C2184：  
  
```  
// C2184.cpp void f() { int * p; __try{} __except(p){};   // C2184 }  
```  
  
 可能的解决方法：  
  
```  
// C2184b.cpp // compile with: /c void f() { int i = 0; __try{} __except(i){}; }  
```