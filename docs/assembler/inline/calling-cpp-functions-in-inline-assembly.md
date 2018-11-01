---
title: 在内联汇编程序内调用 C++ 函数
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 666f7b2a59f0d48a14be54a439b6402f2a4d3128
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458214"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在内联汇编程序内调用 C++ 函数

**Microsoft 专用**

`__asm` 块只能调用未重载的全局 C++ 函数。 如果调用重载的全局 C++ 函数或 C++ 成员函数，则编译器会发出错误。

您还可以调用任何函数使用声明**extern"C"** 链接。 这允许`__asm`块内调用 C 库函数，因为所有标准标头文件都声明库函数具有 c + + 程序**extern"C"** 链接。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>