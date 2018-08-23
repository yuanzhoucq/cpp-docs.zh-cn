---
title: .FPO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df5185c0dc699764427989b2f46345d90ded1729
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055920"
---
# <a name="fpo"></a>.FPO
。FPO 指令控制调试记录与.debug$ F 段或部分显示。  
  
## <a name="syntax"></a>语法  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### <a name="parameters"></a>参数  
 `cdwLocals`  
 无符号的 32 位值的本地变量数。  
  
 `cdwParams`  
 Dword 值，一个 16 位无符号的值中的参数的大小。  
  
 *cbProlog*  
 在函数 prolog 代码中，一个 8 位无符号的值的字节数。  
  
 `cbRegs`  
 保存的寄存器号。  
  
 `fUseBP`  
 指示是否已分配的 EBP 寄存器。 0 或 1。  
  
 *cbFrame*  
 指示的帧类型。  请参阅[FPO_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)