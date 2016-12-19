---
title: "编译器警告（等级 1）C4077 | Microsoft Docs"
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
  - "C4077"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4077"
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4077
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未知的 check\_stack 选项  
  
 旧式 **check\_stack** 杂注与未知的参数一起使用。 参数必须为 `+`、`-`、`(on)`、`(off)` 或为空。  
  
 编译器将忽略杂注，保持堆栈检查不变。  
  
## 示例  
  
```  
// C4077.cpp // compile with: /W1 /LD #pragma check_stack yes // C4077 #pragma check_stack +    // Correct old form #pragma check_stack (on) // Correct new form  
```