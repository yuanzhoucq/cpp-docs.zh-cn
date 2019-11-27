---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 08bc5ab50e15aa59e0c49992d1810c7de20f364e
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397952"
---
# <a name="savexmm128"></a>.SAVEXMM128

为指定的 XMM register 生成 `UWOP_SAVE_XMM128` 或 `UWOP_SAVE_XMM128_FAR` 展开代码项，并使用当前的序言偏移量偏移。 MASM 将选择最有效的编码。

## <a name="syntax"></a>语法

> **.SAVEXMM128** *xmmreg* ，*偏移量*

## <a name="remarks"></a>备注

**.SAVEXMM128**允许 ml64.exe 用户指定框架函数的展开方式，并且仅允许在序言中使用，该函数从[过程](../../assembler/masm/proc.md)框架声明扩展到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 .SAVEXMM128 后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

*偏移量*必须是16的倍数。

有关详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
