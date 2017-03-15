---
title: "MxCsr | Microsoft Docs"
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
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# MxCsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

寄存器状态还包括 MxCsr。  调用约定将此寄存器分为易失部分和非易失部分。  易失部分包含 6 种状态标志 MXCSR\[0:5\]，而寄存器的其余部分 MXCSR\[6:15\] 被视为非易失部分。  
  
 在开始执行程序时，非易失部分被设置为下列标准值：  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 修改 MXCSR 中任何非易失字段的被调用方在将这些字段返回给其调用方之前必须还原它们。  此外，已修改其中任何字段的调用方在调用被调用方之前必须将它们还原为其标准值，除非依照约定被调用方需要修改后的值。  
  
 对于控制标志的非易失性规则有两个例外：  
  
-   在函数中，给定函数的认可目的是修改非易失 MxCsr 标志。  
  
-   如果已经证明，违反这些规则产生的程序（的行为）与未违反这些规则产生的程序（的行为）相同（例如通过分析整个程序）。  
  
 无法跨函数边界假设 MXCSR 的易失部分的状态，除非在函数的文档中特别说明。  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)