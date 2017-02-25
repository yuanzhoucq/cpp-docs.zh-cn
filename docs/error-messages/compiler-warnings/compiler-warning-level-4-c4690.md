---
title: "编译器警告（等级 4）C4690 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4690"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4690"
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 4）C4690
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[ emitidl\( pop \) \]: 出栈的比入栈的多  
  
 [emitidl](../../windows/emitidl.md) 特性的出栈次数比入栈次数多一次。  
  
## 示例  
 下面的示例生成 C4690。  
  
```  
// C4690.cpp // compile with: /c /W4 [emitidl(pop)];   // C4690 class x {};  
```