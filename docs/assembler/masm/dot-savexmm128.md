---
title: ".SAVEXMM128 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEXMM128
dev_langs: C++
helpviewer_keywords: .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384615a0c58c3c28a2e0958d6909546f5753ce6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="savexmm128"></a>.SAVEXMM128
生成或者`UWOP_SAVE_XMM128`或`UWOP_SAVE_XMM128_FAR`展开代码条目指定的 XMM 寄存器和偏移量使用当前的序言偏移量。 MASM 将选择最有效的编码。  
  
## <a name="syntax"></a>语法  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>备注  
 .SAVEXMM128 允许 ml64.exe 用户指定如何帧函数展开，并只允许在序言从内[PROC](../../assembler/masm/proc.md)帧声明移到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们仅生成`.xdata`和`.pdata`。 .SAVEXMM128 前面应带有实际实现的操作要展开的说明。 它是一个包装展开指令和它们专用于在宏中展开以确保协议的代码的好办法。  
  
 `offset`必须是 16 的倍数。  
  
 有关详细信息，请参阅[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)