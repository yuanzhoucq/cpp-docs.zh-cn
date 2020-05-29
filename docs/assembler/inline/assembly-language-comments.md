---
title: 汇编语言注释
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169599"
---
# <a name="assembly-language-comments"></a>汇编语言注释

**Microsoft 专用**

`__asm` 块中的指令可使用汇编语言注释：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由于 C 宏会扩展为单个逻辑行，因此应避免在宏中使用汇编语言注释。 （请参阅将[__Asm 块定义为 C 宏](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。）`__asm` 块还可以包含 C 样式注释;有关详细信息，请参阅[在 __Asm C++块中使用 C 或](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
