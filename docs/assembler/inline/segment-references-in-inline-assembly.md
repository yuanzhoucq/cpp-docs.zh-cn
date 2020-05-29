---
title: 内联程序集中的段引用
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169248"
---
# <a name="segment-references-in-inline-assembly"></a>内联程序集中的段引用

**Microsoft 专用**

必须按寄存器而不是按名称引用段（例如，段名 `_TEXT` 是无效的）。 段重写必须显式使用寄存器，就像在 ES:[BX] 中一样。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
