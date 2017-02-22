---
title: "NMAKE 错误 U1099 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1099"
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# NMAKE 错误 U1099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆栈溢出（Stack Overflow）  
  
 正被处理的生成文件对于 NMAKE 中的当前堆栈分配已太复杂。  NMAKE 具有 0x3000 \(12K\) 的分配。  
  
 若要增加 NMAKE 的堆栈分配，请通过较大的堆栈选项来运行 [editbin \/stack](../../build/reference/stack.md) 实用工具：  
  
 **editbin \/STACK:reserve NMAKE.EXE**  
  
 其中的 *reserve* 是大于 NMAKE 中当前堆栈分配的数。