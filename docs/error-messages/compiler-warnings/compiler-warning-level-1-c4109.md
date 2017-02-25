---
title: "编译器警告（等级 1）C4109 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4109"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4109"
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4109
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的标识符“identifier”  
  
 忽略包含意外标识符的杂注。  
  
## 示例  
  
```  
// C4109.cpp // compile with: /W1 /LD #pragma init_seg( abc ) // C4109  
```