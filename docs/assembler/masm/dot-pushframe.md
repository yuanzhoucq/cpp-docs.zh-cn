---
title: .PUSHFRAME
ms.date: 08/30/2018
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: b0f047278f6250d5ef359f7992df4ea23f4bbd9b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398046"
---
# <a name="pushframe"></a>.PUSHFRAME

生成 `UWOP_PUSH_MACHFRAME` 展开代码项。 如果指定了可选*代码*，则为展开代码条目指定修饰符1。 否则，修饰符为0。

## <a name="syntax"></a>语法

> **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME** ⟦*code*⟧;;

## <a name="remarks"></a>备注

.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME 允许 ml64.exe 用户指定框架函数的展开方式，并只允许在序言内进行扩展，这种情况下，它从[过程](../../assembler/masm/proc.md)框架声明扩展到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 **.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME**后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

有关详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
