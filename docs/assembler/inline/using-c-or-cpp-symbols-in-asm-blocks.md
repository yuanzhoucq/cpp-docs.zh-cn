---
title: 在 __asm 块中使用 C 或 C++ 符号
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: ecdd3b6b6916a5c9585678838d8e494a58e0508c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191191"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>在 __asm 块中使用 C 或 C++ 符号

**Microsoft 专用**

**`__asm`** 块可引用范围中出现块的任何 C 或 c + + 符号。 （C 和 c + + 符号是变量名、函数名和标签，即不是符号常量或成员的名称 **`enum`** 。 您不能调用 C++ 成员函数。）

 C 和 C++ 符号的使用有一些限制：

- 每个汇编语言语句只能包含一个 C 或 C++ 符号。 多个符号只能与**长度**、**类型**和**大小**表达式出现在同一程序集指令中。

- 块中引用的函数 **`__asm`** 必须在程序的前面声明（原型）。 否则，编译器无法区分块中的函数名和标签 **`__asm`** 。

- **`__asm`** 块不能将任何 C 或 c + + 符号与 MASM 保留字的拼写相同（无论大小写）。 MASM 保留字包括指令名称（如**推送**和寄存器名称，如 SI）。

- 在块中无法识别结构和联合标记 **`__asm`** 。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
