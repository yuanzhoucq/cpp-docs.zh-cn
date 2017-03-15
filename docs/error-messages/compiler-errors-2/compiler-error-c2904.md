---
title: "编译器错误 C2904 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2904"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2904"
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2904
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：名称已经用于当前范围内的模板  
  
 检查代码中是否有重复的名称。  
  
 以下示例生成 C2904：  
  
```  
// C2904.cpp // compile with: /c void X();  // X is declared as a function template<class T> class X{};  // C2904  
```