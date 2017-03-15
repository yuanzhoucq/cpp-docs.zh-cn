---
title: "ML Nonfatal Error A2008 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2008"
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**语法错误:**  
  
 在当前位置的标记导致语法错误。  
  
 操作之一可能发生:  
  
-   带前缀将添加到或从指令省略。  
  
-   保留字 \(例如 **C** 或 **范围**\) 被用作标识符。  
  
-   的命令为当前处理器或协处理器选择不可用改用。  
  
-   比较运行时运算符 \(例如 `==`\) 用于一个条件的语句而不是关系运算符 \(例如 [EQ](../../assembler/masm/operator-eq.md)\)。  
  
-   为命令或指令很少操作数。  
  
-   使用已过时指令。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)