---
title: .SAVEREG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEREG
dev_langs:
- C++
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a50b7a91efd7069e148222d3e3da44178974d6ba
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055201"
---
# <a name="savereg"></a>.SAVEREG
生成或者`UWOP_SAVE_NONVOL`或`UWOP_SAVE_NONVOL_FAR`展开代码条目指定的寄存器 (`reg`) 和偏移量 (`offset`) 使用的当前序言偏移量。 MASM 将选择最有效的编码。  
  
## <a name="syntax"></a>语法  
  
```  
.SAVEREG reg, offset  
```  
  
## <a name="remarks"></a>备注  
 .SAVEREG 允许 ml64.exe 用户指定如何帧函数展开，并只允许在序言从内[PROC](../../assembler/masm/proc.md)帧声明移到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们仅生成`.xdata`和`.pdata`。 .SAVEREG 前面应带有实际实现的操作要展开的说明。 它是一个包装展开指令和它们专用于在宏中展开以确保协议的代码的好办法。  
  
 有关详细信息，请参阅[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)