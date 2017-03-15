---
title: "ML Nonfatal Error A2006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2006"
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**未定义的符号:标识符**  
  
 尝试使用未定义的符号。  
  
 操作之一可能发生:  
  
-   符号未定义。  
  
-   字段不是指定的结构的成员。  
  
-   符号在不包括的包含文件中定义。  
  
-   一个外部符号使用，既没有 [外部](../../assembler/masm/extern-masm.md) 或 [EXTERNDEF](../../assembler/masm/externdef.md) 指令。  
  
-   符号名称拼写错误。  
  
-   本地代码标签引用在其范围内。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)