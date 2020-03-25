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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169573"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在内联汇编程序内调用 C++ 函数

**Microsoft 专用**

`__asm` 块只能调用未重载的全局 C++ 函数。 如果调用重载的全局 C++ 函数或 C++ 成员函数，则编译器会发出错误。

还可以调用用**extern "C"** 链接声明的任何函数。 这允许C++程序中的 `__asm` 块调用 C 库函数，因为所有标准标头文件都将库函数声明为具有**extern "C"** 链接。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>
