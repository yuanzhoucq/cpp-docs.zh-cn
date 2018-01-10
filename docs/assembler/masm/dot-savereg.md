---
title: ".SAVEREG |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEREG
dev_langs: C++
helpviewer_keywords: .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab1e777aa8bdddc4aa4fd71212f3275231b92dc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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