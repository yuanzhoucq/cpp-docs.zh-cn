---
title: .PUSHFRAME
description: 描述。SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME MASM 指令，用于指定如何展开帧函数。
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 5f951396291ecb12dab500a364f176106c5daa8b
ms.sourcegitcommit: 2cac0150ab3bc8260f866451019b8e22c7e1ac11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945847"
---
# <a name="pushframe"></a>.PUSHFRAME

生成 `UWOP_PUSH_MACHFRAME` 展开代码项。 如果指定了可选的**代码**关键字，则为展开代码条目指定修饰符1。 否则，修饰符为0。

## <a name="syntax"></a>语法

> **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME** ⟦**CODE**⟧;;

## <a name="remarks"></a>备注

.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME 允许 ml64.exe 用户指定框架函数的展开方式。 只允许在序言中使用，它从[过程](../../assembler/masm/proc.md)框架声明扩展到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME**后面应是实际实现要展开的操作的说明。 最好将展开指令和要展开的代码中的代码包装在一起，以确保协议。

有关详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
