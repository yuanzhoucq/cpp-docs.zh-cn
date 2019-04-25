---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: cac7aa7f2bdbf6b60831d2beb062f86559ec0358
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178158"
---
# <a name="savereg"></a>.SAVEREG

生成任一`UWOP_SAVE_NONVOL`或`UWOP_SAVE_NONVOL_FAR`展开代码指定的注册条目 (`reg`) 和偏移量 (`offset`) 使用当前的序言偏移量。 MASM 会选择最有效的编码。

## <a name="syntax"></a>语法

> .SAVEREG reg、 偏移量

## <a name="remarks"></a>备注

.SAVEREG 允许 ml64.exe 用户指定帧函数的展开时，并只允许在从序言[PROC](../../assembler/masm/proc.md)帧声明到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们只能生成`.xdata`和`.pdata`。 .SAVEREG 前面应带有实际实现是展开的操作的说明。 它是包装展开指令和它们专门为在宏展开用于确保协议的代码的好办法。

有关详细信息，请参阅[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>