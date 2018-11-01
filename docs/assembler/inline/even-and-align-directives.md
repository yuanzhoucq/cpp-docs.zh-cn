---
title: EVEN 和 ALIGN 指令
ms.date: 08/30/2018
f1_keywords:
- align
- EVEN
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 522d5689d680d0fc334743d2802abe21570dd6f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604344"
---
# <a name="even-and-align-directives"></a>EVEN 和 ALIGN 指令

**Microsoft 专用**

尽管内联汇编程序不支持大多数 MASM 指令，但它确实支持`EVEN`并**对齐**。 这些指令放**NOP** （无操作），以将标签与特定边界对齐的程序集代码中的说明。 对某些处理器来说，这使得指令取回操作更加有效。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>