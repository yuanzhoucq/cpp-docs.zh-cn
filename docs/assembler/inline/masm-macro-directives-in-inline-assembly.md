---
title: 内联程序集中的 MASM 宏指令 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35ad22a9a4b79a31665ab6b156f8174d395bb0ee
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687968"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>内联程序集中的 MASM 宏指令

**Microsoft 专用**

内联汇编程序不是宏汇编程序。 不能使用 MASM 宏指令 (**宏**， `REPT`， **IRC**， `IRP`，以及`ENDM`) 或宏运算符 (**<>**，**!**， **&**， `%`，并`.TYPE`)。 但是，`__asm` 块可以使用 C 预处理器指令。 请参阅[使用 C 或 c + + 在 __asm 块中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)有关详细信息。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>