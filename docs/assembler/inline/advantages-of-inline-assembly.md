---
title: 内联汇编的优点
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: ecf1598ec90a8600e1fa9aae565724c254dc11e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167394"
---
# <a name="advantages-of-inline-assembly"></a>内联汇编的优点

**Microsoft 专用**

由于内联汇编程序不需要单独的程序集和链接步骤，因此它比单独的汇编程序更方便。 内联程序集代码可以使用任何 C 变量或范围中的函数名，因此，将其与程序的 C 代码集成非常容易。 由于程序集代码可与 C 或 C++ 语句内联组合，因此它可以执行在 C 或 C++ 中难以完成或无法完成的任务。

内联程序集的用法包括：

- 使用汇编语言编写函数。

- 代码的点优化速度临界区。

- 通过硬件直接访问设备驱动程序。

- 为“naked”调用编写 prolog 和 epilog 代码。

内联程序集是一个具有特殊用途的工具。 如果你计划通过端口将应用程序传输到其他计算机，你可能需要在单独的模块中放置计算机特定的代码。 由于内联汇编程序不支持任何 Microsoft 宏汇编程序 (MASM) 的宏和数据指令，因此您可能会发现对此类模块使用 MASM 会更方便。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>