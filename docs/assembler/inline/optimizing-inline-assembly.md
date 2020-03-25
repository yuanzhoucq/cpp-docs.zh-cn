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
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169261"
---
# <a name="optimizing-inline-assembly"></a>优化内联汇编程序

**Microsoft 专用**

如果函数中存在 `__asm` 块，则会在多个方面影响优化。 首先，编译器不会尝试优化 `__asm` 块本身。 您在汇编语言中编写的内容就是您获得的内容。 第二，存在 `__asm` 块将影响寄存器变量存储。 如果寄存器的内容将被 `__asm` 块更改，编译器将避免在 `__asm` 块中注册变量。 最后，其他某些函数范围的优化将受函数中包含的汇编语言的影响。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>
