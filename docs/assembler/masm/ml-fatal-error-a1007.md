---
title: "ML Fatal Error A1007 | Microsoft Docs"
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
  - "A1007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1007"
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Fatal Error A1007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**嵌套级别太深**  
  
 此时将汇编已到达其嵌套限制。  限制否则为 20 个级别除非特别说明。  
  
 以下任一嵌套太深:  
  
-   一个高级指令例如 [.IF](../../assembler/masm/dot-if.md)、 [.REPEAT](../../assembler/masm/dot-repeat.md)或 [.WHILE](../../assembler/masm/dot-while.md)。  
  
-   结构定义。  
  
-   条件程序集指令。  
  
-   程序定义。  
  
-   [PUSHCONTEXT](../../assembler/masm/pushcontext.md) 指令 \(限制为 10\)。  
  
-   段定义。  
  
-   包含文件。  
  
-   宏。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)