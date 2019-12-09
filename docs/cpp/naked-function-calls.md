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
ms.openlocfilehash: 242fe83807c6608a09492d0f1f817e3b6e50e530
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857393"
---
# <a name="naked-function-calls"></a>Naked 函数调用

**Microsoft 专用**

使用**naked**特性声明的函数会在没有 prolog 或 epilog 代码的情况下发出，使你能够使用[内联汇编程序](../assembler/inline/inline-assembler.md)编写你自己的自定义 prolog/epilog 序列。 将裸函数作为高级功能提供。 利用这些函数，您可以声明从 C/C++ 之外的上下文中调用的函数，从而作出有关参数位置或保留哪些寄存器的各种假设。 示例包括例程（如中断处理程序）。 此功能对于虚拟设备驱动程序 (VxDs) 的编写器特别有用。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [naked](../cpp/naked-cpp.md)

- [裸函数的规则和限制](../cpp/rules-and-limitations-for-naked-functions.md)

- [有关编写 Prolog/Epilog 代码的注意事项](../cpp/considerations-for-writing-prolog-epilog-code.md)

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[调用约定](../cpp/calling-conventions.md)