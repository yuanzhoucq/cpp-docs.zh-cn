---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: c29ec47170c5e0f46f02d53f23ab477a79bbdc32
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507895"
---
# <a name="savexmm128"></a>.SAVEXMM128

生成任一`UWOP_SAVE_XMM128`或`UWOP_SAVE_XMM128_FAR`展开指定 XMM 寄存器的代码项以及使用当前的序言偏移的偏移量。 MASM 会选择最有效的编码。

## <a name="syntax"></a>语法

> .savexmm128 xmmreg、 偏移量

## <a name="remarks"></a>备注

.SAVEXMM128 允许 ml64.exe 用户指定帧函数如何将回退，并只允许在序言中，从扩展了[PROC](../../assembler/masm/proc.md)帧声明到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们只能生成`.xdata`和`.pdata`。 .SAVEXMM128 前面应带有实际实现是展开的操作的说明。 它是包装展开指令和它们专门为在宏展开用于确保协议的代码的好办法。

*偏移量*必须是 16 的倍数。

有关详细信息，请参阅[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>