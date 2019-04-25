---
title: 汇编语言注释
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: fc37658eccd99b61d45aa9a9a7a2675ef90eee89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167239"
---
# <a name="assembly-language-comments"></a>汇编语言注释

**Microsoft 专用**

`__asm` 块中的指令可使用汇编语言注释：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由于 C 宏会扩展为单个逻辑行，因此应避免在宏中使用汇编语言注释。 (请参阅[__asm 块定义为 C 宏](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。)`__asm`块也可包含 C 样式注释; 有关详细信息，请参阅[使用 C 或C++在 __asm 块中](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>