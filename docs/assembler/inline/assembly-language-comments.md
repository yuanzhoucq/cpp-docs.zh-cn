---
title: 汇编语言注释
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: 2e993bd48c7ec801abd440676c80a5bd8f7b42ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192725"
---
# <a name="assembly-language-comments"></a>汇编语言注释

**Microsoft 专用**

块中的说明 **`__asm`** 可以使用汇编语言注释：

```cpp
__asm mov ax, offset buff ; Load address of buff
```

由于 C 宏会扩展为单个逻辑行，因此应避免在宏中使用汇编语言注释。 （请参阅将[__Asm 块定义为 C 宏](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。）**`__asm`** 块还可以包含 C 样式注释; 有关详细信息，请参阅[在 __asm 块中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
