---
title: "编译器错误 C2161 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2161"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2161"
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2161
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\#\#”不能在宏定义的结尾处出现  
  
 以标记粘贴运算符结尾 \(\#\#\) 的宏定义。  
  
 以下示例生成 C2161：  
  
```  
// C2161.cpp // compile with: /c #define mac(a,b) a   // OK #define mac(a,b) a##   // C2161  
```