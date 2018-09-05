---
title: 将 __asm 块定义为 C 宏 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cb9ef740ec8b521771c84a1edd194a6ee6ace4f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683092"
---
# <a name="defining-asm-blocks-as-c-macros"></a>将 __asm 块定义为 C 宏

**Microsoft 专用**

利用 C 宏，可以轻松将程序集代码插入源代码中，但执行此操作时要格外小心，因为宏会扩展到单个逻辑行中。 若要创建可靠的宏，请遵循以下规则：

- 将 `__asm` 块括在大括号内。

- 将 `__asm` 关键字放在每个程序集指令的前面。

- 使用旧式 C 注释 (`/* comment */`) 而不是程序集样式的注释 (`; comment`) 或单行 C 注释 (`// comment`)。

为了演示这一点，下面的示例定义一个简单的宏：

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

乍一看，最后三个 `__asm` 关键字是多余的。 但它们是必需的，因为宏将扩展到单个行中：

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

需要将第三个和第四个 `__asm` 关键字作为语句分隔符。 在 `__asm` 块中识别的唯一语句分隔符是换行符和 `__asm` 关键字。 由于定义为宏的块是一个逻辑行，因此您必须使用 `__asm` 分隔每个指令。

大括号也是必需的。 如果省略它们，则编译器会对同一行上的 C 或 C++ 语句与宏调用的右侧内容混淆不清。 在没有右大括号的情况下，编译器无法告知程序集代码停止的位置，并且会将 `__asm` 块后面的 C 或 C++ 语句视为程序集指令。

使用分号启动的程序集样式注释 (**;**) 继续到行尾。 这会导致宏出现问题，因为编译器将忽略注释后面的内容，直到到达逻辑行尾。 上述情况同样适用于单行 C 或 C++ 注释 (`// comment`)。 若要防止错误，请在定义为宏的 `/* comment */` 块中使用旧式 C 注释 (`__asm`)。

编写为 C 宏的 `__asm` 块可以采用参数。 但与普通 C 宏不同，`__asm` 宏不能返回值。 这样您便无法在 C 或 C++ 表达式中使用这些宏。

请注意，不要任意调用此类型的宏。 例如，调用使用 `__fastcall` 约定声明的函数中的汇编语言宏可能会导致意外的结果。 (请参阅[使用和保留内联程序集中的寄存器](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)。)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>