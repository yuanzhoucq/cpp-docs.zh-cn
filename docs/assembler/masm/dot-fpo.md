---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: ec08be4941f81abed55420884b34dc817caf3f13
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317729"
---
# <a name="fpo-32-bit-masm"></a>.FPO （32位 MASM）

**。FPO**指令控制将调试记录的辐射到. debug $ F 段或部分。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **.FPO** （*cdwLocals*， *cdwParams*， *cbProlog*， *cbRegs*， *fUseBP*， *cbFrame*）

### <a name="parameters"></a>参数

*cdwLocals*\
局部变量数，即无符号32位值。

*cdwParams*\
DWORD 中参数的大小，无符号的16位值。

*cbProlog*\
函数 prolog 代码中的字节数，无符号8位值。

*cbRegs*\
已保存编号寄存器。

*fUseBP*\
指示是否已分配 EBP 寄存器。 0或1。

*cbFrame*\
指示帧类型。  有关详细信息，请参阅[FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
