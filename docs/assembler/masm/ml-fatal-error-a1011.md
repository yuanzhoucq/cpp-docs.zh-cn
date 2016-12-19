---
title: "ML Fatal Error A1011 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1011"
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Fatal Error A1011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**指令必须在中控制块**  
  
 此时将汇编找到了一个方不应出现的高级指令。  找到下列指令之一:  
  
-   不 [.IF](../../assembler/masm/dot-if.md)的[.ELSE](../../assembler/masm/dot-else.md)  
  
-   不 [.IF](../../assembler/masm/dot-if.md)的[.ENDIF](../../assembler/masm/dot-endif.md)  
  
-   不 [.WHILE](../../assembler/masm/dot-while.md)的[.ENDW](../../assembler/masm/dot-endw.md)  
  
-   不 [.REPEAT](../../assembler/masm/dot-repeat.md)的[.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)  
  
-   不 [.WHILE](../../assembler/masm/dot-while.md) 或 [.REPEAT](../../assembler/masm/dot-repeat.md)的[.CONTINUE](../../assembler/masm/dot-continue.md)  
  
-   不 [.WHILE](../../assembler/masm/dot-while.md) 或 [.REPEAT](../../assembler/masm/dot-repeat.md)的[.BREAK](../../assembler/masm/dot-break.md)  
  
-   在 `.ELSE`后的[.ELSE](../../assembler/masm/dot-else.md)  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)