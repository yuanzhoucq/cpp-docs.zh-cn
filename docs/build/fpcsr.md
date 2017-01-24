---
title: "FpCsr | Microsoft Docs"
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
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# FpCsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

寄存器状态还包括 x87 FPU 控制字。  调用约定指出此寄存器是非易失的。  
  
 在开始执行程序时，x87 FPU 控制字寄存器设置为下列标准值：  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved – 0  
FPCSR[8:9]: Precision Control – 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control – 0 (not used)  
```  
  
 修改 FPCSR 中任何字段的被调用方在将这些字段返回给其调用方之前必须还原它们。  此外，已修改其中任何字段的调用方在调用被调用方之前必须将它们还原为其标准值，除非依照约定被调用方需要修改后的值。  
  
 对于控制标志的非易失性规则有两个例外：  
  
1.  在函数中，给定函数的认可目的是修改非易失的 FpCsr 标志。  
  
2.  如果已经证明，违反这些规则产生的程序（的行为）与未违反这些规则产生的程序（的行为）相同（例如通过分析整个程序）。  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)