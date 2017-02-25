---
title: "GOTO (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "goto"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GOTO directive"
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# GOTO (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用程序集添加到行标记为的 **:***macrolabel*。  
  
## 语法  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## 备注  
 **导航** 只允许在 [宏](../../assembler/masm/macro.md)， [为](../../assembler/masm/for-masm.md)， [FORC](../../assembler/masm/forc.md)， [重复](../../assembler/masm/repeat.md)内，并且， **while** 块。  标签必须位于行的唯一指令，并且必须在前导的冒号之后。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)