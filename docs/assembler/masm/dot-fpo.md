---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 83d6e81ea7dd35038f27f2721f3cc41fe49ef1bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204053"
---
# <a name="fpo"></a>.FPO

。FPO 指令控制调试与.debug$ F 段或部分的记录的显示。

## <a name="syntax"></a>语法

> FPO (*cdwLocals*， *cdwParams*， *cbProlog*， *cbRegs*， *fUseBP*， *cbFrame*)

### <a name="parameters"></a>参数

*cdwLocals*<br/>
无符号的 32 位值的本地变量的数量。

*cdwParams*<br/>
Dword 值，无符号 16 位值中的参数的大小。

*cbProlog*<br/>
在函数 prolog 代码中，无符号 8 位值的字节数。

*cbRegs*<br/>
保存的寄存器号。

*fUseBP*<br/>
指示是否已分配的 EBP 寄存器。 0 或 1。

*cbFrame*<br/>
指示的帧类型。  请参阅[FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data)有关详细信息。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>