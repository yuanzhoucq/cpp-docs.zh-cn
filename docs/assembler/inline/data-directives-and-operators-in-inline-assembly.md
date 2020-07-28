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
ms.openlocfilehash: bcacb0cdd26181da3cf80a582866c1e30567d043
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192348"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>内联程序集中的数据指令和运算符

**Microsoft 专用**

尽管 **`__asm`** 块可以引用 c 或 c + + 数据类型和对象，但它不能使用 MASM 指令或运算符来定义数据对象。 具体而言，不能使用定义指令**DB**， `DW` ， **DD**，，，， `DQ` `DT` `DF` 或运算符 `DUP` 或**THIS**。 MASM 结构和记录也不可用。 内联汇编程序不接受指令 `STRUC` 、 `RECORD` 、**宽度**或**掩码**。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
