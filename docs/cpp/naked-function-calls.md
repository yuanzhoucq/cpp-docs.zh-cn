---
title: Naked 函数调用
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 9b49d34d7276d3c9260488f23d1821b9708d2481
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227317"
---
# <a name="naked-function-calls"></a>Naked 函数调用

**Microsoft 专用**

使用特性声明的函数 **`naked`** 会在没有 prolog 或 epilog 代码的情况下发出，使你能够使用[内联汇编程序](../assembler/inline/inline-assembler.md)编写你自己的自定义 prolog/epilog 序列。 将裸函数作为高级功能提供。 利用这些函数，您可以声明从 C/C++ 之外的上下文中调用的函数，从而作出有关参数位置或保留哪些寄存器的各种假设。 示例包括例程（如中断处理程序）。 此功能对于虚拟设备驱动程序 (VxDs) 的编写器特别有用。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [naked](../cpp/naked-cpp.md)

- [裸函数的规则和限制](../cpp/rules-and-limitations-for-naked-functions.md)

- [编写 Prolog/Epilog 代码的注意事项](../cpp/considerations-for-writing-prolog-epilog-code.md)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[调用约定](../cpp/calling-conventions.md)
