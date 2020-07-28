---
title: 优化内联汇编程序
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: a558761ff49c2b508a5bad6172cda2283801e30e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191724"
---
# <a name="optimizing-inline-assembly"></a>优化内联汇编程序

**Microsoft 专用**

**`__asm`** 函数中的块存在通过多种方式影响优化。 首先，编译器不会尝试优化 **`__asm`** 块本身。 您在汇编语言中编写的内容就是您获得的内容。 其次，存在 **`__asm`** 块会影响寄存器变量存储。 **`__asm`** 如果寄存器的内容会被块更改，编译器将避免在块中使用局部变量变量 **`__asm`** 。 最后，其他某些函数范围的优化将受函数中包含的汇编语言的影响。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>
