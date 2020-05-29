---
title: EVEN 和 ALIGN 指令
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: b191ce0942d7596090bfd7948a37a5c9e6aac15e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169430"
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指令

**Microsoft 专用**

尽管内联汇编程序不支持大多数 MASM 指令，但它确实支持 `EVEN` 和**对齐**。 这些指令根据需要将**NOP** （无操作）指令置于程序集代码中，以便将标签与特定边界对齐。 对某些处理器来说，这使得指令取回操作更加有效。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
