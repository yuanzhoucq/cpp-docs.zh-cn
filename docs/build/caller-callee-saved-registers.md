---
title: "由调用方或被调用方保存的寄存器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 由调用方或被调用方保存的寄存器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

寄存器 RAX、RCX、RDX、R8、R9、R10、R11 被视为易失的，并且必须在函数调用时视为已销毁（除非通过全程序优化等分析被认定为安全的）。  
  
 寄存器 RBX、RBP、RDI、RSI、RSP、R12、R13、R14 和 R15 被视为非易失的，必须由使用它们的函数进行保存和还原。  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)