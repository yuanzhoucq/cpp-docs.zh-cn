---
title: "setjmp/longjump | Microsoft Docs"
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
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setjmp/longjump
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包括 setjmpex.h 或 setjmp.h 时，对 [setjmp](../c-runtime-library/reference/setjmp.md) 或 [longjmp](../c-runtime-library/reference/longjmp.md) 的所有调用都将导致一个展开操作，该操作将调用析构函数并终止调用。  这不同于 x86，x86 中的 setjmp.h 将产生 finally 子句，但不会调用析构函数。  
  
 对 `setjmp` 的调用会保存当前堆栈指针、非易失寄存器和 MxCsr 寄存器。  对 `longjmp` 的调用将返回最近一次 `setjmp` 调用的位置，并将堆栈指针、非易失寄存器和 MxCsr 寄存器重置回最近一次 `setjmp` 调用保存的状态。  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)