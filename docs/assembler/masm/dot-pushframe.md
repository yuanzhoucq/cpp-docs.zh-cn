---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 9ea506e25435c5d6f1b10eab8c4f25f72bf88791
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178431"
---
# <a name="pushframe"></a>.PUSHFRAME

生成`UWOP_PUSH_MACHFRAME`展开代码项。 如果可选`code`指定，则展开代码项提供的修饰符为 1。 否则修饰符为 0。

## <a name="syntax"></a>语法

> .PUSHFRAME [code]

## <a name="remarks"></a>备注

.PUSHFRAME 允许 ml64.exe 用户指定帧函数的展开时，并只允许在从序言[PROC](../../assembler/masm/proc.md)帧声明到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们只能生成`.xdata`和`.pdata`。 .PUSHFRAME 前面应带有实际实现是展开的操作的说明。 它是包装展开指令和它们专门为在宏展开用于确保协议的代码的好办法。

有关详细信息，请参阅[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>