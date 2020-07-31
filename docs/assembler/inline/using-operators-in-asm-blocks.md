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
ms.openlocfilehash: cdcfee20cfdc5a6dc315d00ef024d1616900a2e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191100"
---
# <a name="using-operators-in-__asm-blocks"></a>在 __asm 块中使用运算符

**Microsoft 专用**

**`__asm`** 块不能使用 c 或 c + + 特定运算符，如 **<<** 运算符。 但是，C 和 MASM 共享的运算符（如 \* 运算符）被解释为汇编语言运算符。 例如，在块外 **`__asm`** ，方括号（**[]**）被解释为封闭数组下标，C 会自动缩放为数组中元素的大小。 在 **`__asm`** 块内部，它们被视为 MASM 索引运算符，该运算符从任何数据对象或标签（而不仅仅是数组）生成未缩放的字节偏移量。 下面的代码阐释了差异：

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

## <a name="see-also"></a>请参阅

[在 __asm 块中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
