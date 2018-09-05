---
title: 汇编语言注释 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02f4c493bac5c2a066dc0b24e2a566d49345288d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683321"
---
# <a name="assembly-language-comments"></a>汇编语言注释

**Microsoft 专用**

`__asm` 块中的指令可使用汇编语言注释：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由于 C 宏会扩展为单个逻辑行，因此应避免在宏中使用汇编语言注释。 (请参阅[__asm 块定义为 C 宏](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。)`__asm`块也可包含 C 样式注释; 有关详细信息，请参阅[使用 C 或 c + + 在 __asm 块中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>