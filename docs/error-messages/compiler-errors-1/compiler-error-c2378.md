---
title: "编译器错误 C2378 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2378"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2378"
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2378
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：重定义；符号不能使用 typedef 重载  
  
 标识符已重定义为 `typedef`。  
  
 下面的示例生成 C2378：  
  
```  
// C2378.cpp // compile with: /c int i; typedef int i;   // C2378 typedef int b;   // OK  
```