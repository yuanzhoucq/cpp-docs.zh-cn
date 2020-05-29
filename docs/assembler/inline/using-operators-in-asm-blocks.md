---
title: 在 __asm 块中使用运算符
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169092"
---
# <a name="using-operators-in-__asm-blocks"></a>在 __asm 块中使用运算符

**Microsoft 专用**

`__asm` 块不能使用 C 或C++特定运算符，如 **<<** 运算符。 但是，C 和 MASM 共享的运算符（如 \* 运算符）被解释为汇编语言运算符。 例如，在 `__asm` 块外，方括号（ **[]** ）被解释为封闭数组下标，C 会自动缩放为数组中元素的大小。 在 `__asm` 块的内部，它们被视为 MASM 索引运算符，该运算符将从任何数据对象或标签（不仅仅是数组）中生成未缩放的字节偏移量。 下面的代码阐释了差异：

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

不缩放对 `array` 的第一个引用，但缩放第二个引用。 请注意，可以使用**TYPE**运算符来实现基于常量的缩放。 例如，以下语句是等价的：

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
