---
title: 内联程序集中的数据指令和运算符
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: 916dce0346bebfc5ff65ca558ae75317a187660a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169534"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>内联程序集中的数据指令和运算符

**Microsoft 专用**

尽管 `__asm` 块可以引用 C 或 C++ 数据类型和对象，但它不能定义具有 MASM 指令或运算符的数据对象。 具体而言，不能使用定义指令**DB**、`DW`、 **DD**、`DQ`、`DT`和 `DF`，也不能 `DUP` 或**此**运算符。 MASM 结构和记录也不可用。 内联汇编程序不接受 `STRUC`、`RECORD`、 **WIDTH**或**MASK**的指令。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
