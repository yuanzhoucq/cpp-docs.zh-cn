---
title: 段中内联程序集的引用 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7add95852f751ed29dad8e0ba9577abd55fabaf
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051471"
---
# <a name="segment-references-in-inline-assembly"></a>内联程序集中的段引用
## <a name="microsoft-specific"></a>Microsoft 专用  
 必须按寄存器而不是按名称引用段（例如，段名 `_TEXT` 是无效的）。 段重写必须显式使用寄存器，就像在 ES:[BX] 中一样。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)