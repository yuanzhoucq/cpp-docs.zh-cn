---
title: "ML Fatal Error A1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1010"
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**不对块嵌套:**  
  
 块开头没有游戏结束，或者块末尾没有匹配的开头。  以下任一能是包含的:  
  
-   一个高级指令例如 [.IF](../../assembler/masm/dot-if.md)、 [.REPEAT](../../assembler/masm/dot-repeat.md)或 [.WHILE](../../assembler/masm/dot-while.md)。  
  
-   一个条件程序集指令例如 [如果](../../assembler/masm/if-masm.md)、 [重复](../../assembler/masm/repeat.md)或 **while**。  
  
-   结构或联合定义。  
  
-   程序定义。  
  
-   段定义。  
  
-   [POPCONTEXT](../../assembler/masm/popcontext.md) 指令。  
  
-   一个条件程序集指令，如、 [ELSEIF](../../assembler/masm/elseif-masm.md)或 **ENDIF** 不匹配的 [如果](../../assembler/masm/if-masm.md)。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)