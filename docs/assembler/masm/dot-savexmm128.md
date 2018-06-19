---
title: .SAVEXMM128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEXMM128
dev_langs:
- C++
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d50d4bbc7f9c89e9ef36a1dd8cf3dfeb56de79b5
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057934"
---
# <a name="savexmm128"></a>.SAVEXMM128
生成或者`UWOP_SAVE_XMM128`或`UWOP_SAVE_XMM128_FAR`展开代码条目指定的 XMM 寄存器和偏移量使用当前的序言偏移量。 MASM 将选择最有效的编码。  
  
## <a name="syntax"></a>语法  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>备注  
 .SAVEXMM128 允许 ml64.exe 用户指定如何帧函数展开，并只允许在序言从内[PROC](../../assembler/masm/proc.md)帧声明移到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们仅生成`.xdata`和`.pdata`。 .SAVEXMM128 前面应带有实际实现的操作要展开的说明。 它是一个包装展开指令和它们专用于在宏中展开以确保协议的代码的好办法。  
  
 `offset` 必须是 16 的倍数。  
  
 有关详细信息，请参阅[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)