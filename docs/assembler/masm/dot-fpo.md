---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3938d9194c35d567ea670e0b92a731193ccd2254
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703790"
---
# <a name="fpo-32-bit-masm"></a>.FPO （32位 MASM）

此.FPO 指令控制将调试记录的辐射到. debug $ F 段或部分。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> FPO （*cdwLocals*， *cdwParams*， *cbProlog*， *cbRegs*， *fUseBP*， *cbFrame*）

### <a name="parameters"></a>参数

*cdwLocals*<br/>
局部变量数，即无符号32位值。

*cdwParams*<br/>
DWORD 中参数的大小，无符号的16位值。

*cbProlog*<br/>
函数 prolog 代码中的字节数，无符号8位值。

*cbRegs*<br/>
已保存编号寄存器。

*fUseBP*<br/>
指示是否已分配 EBP 寄存器。 0或1。

*cbFrame*<br/>
指示帧类型。  有关详细信息，请参阅[FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>
