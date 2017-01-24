---
title: "针对旧代码的浮点支持 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 针对旧代码的浮点支持 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MMX 和浮点堆栈寄存器 \(MM0\-MM7\/ST0\-ST7\) 通过上下文开关保持。  对于这些寄存器，没有显式调用约定。  在内核模式代码中严格禁止使用这些寄存器。  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)