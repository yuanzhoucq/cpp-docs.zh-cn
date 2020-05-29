---
title: 内联程序集中的 MASM 宏指令
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169274"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>内联程序集中的 MASM 宏指令

**Microsoft 专用**

内联汇编程序不是宏汇编程序。 不能使用 MASM 宏指令（**宏**、`REPT`、 **IRC**、`IRP`和 `ENDM`）或宏运算符（ **<>** 、 **！** 、 **&** 、`%`和 `.TYPE`）。 但是，`__asm` 块可以使用 C 预处理器指令。 有关详细信息，请参阅[在 __Asm 块中使用 C 或C++ ](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) 。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
