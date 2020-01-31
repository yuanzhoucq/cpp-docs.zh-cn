---
title: 参数传递和命名约定
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: 1928f8e479b0533c5a8b2e60de7af9eff93f7eed
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222264"
---
# <a name="argument-passing-and-naming-conventions"></a>参数传递和命名约定

**Microsoft 专用**

Microsoft C++编译器，你可以指定传递自变量的约定和返回值的函数和调用方。 并非所有约定都在所有支持的平台上可用，某些约定使用平台特定的实现。 在大多数情况下，将忽略在特定平台上指定不支持的约定的关键字或编译器开关，并将使用平台默认约定。

在 x86 平台上，所有自变量在传递时都将加宽到 32 位。 返回值也将加宽到 32 位，并将通过 EAX 寄存器返回，但在 EDX:EAX 寄存器对中返回的 8 字节结构除外。 更大的结构将在 EAX 寄存器中作为指向隐藏返回结构的指针返回。 参数将从右到左推送到堆栈中。 不是 POD 的结构不会在寄存器中返回。

编译器将生成 prolog 和 epilog 代码来保存并还原 ESI、EDI、EBX 和 EBP 寄存器（如果在函数中使用了它们）。

> [!NOTE]
> 当结构、联合或类由值从函数返回时，类型的所有定义需要相同，否则程序可能在运行时失败。

有关如何定义自己的函数 prolog 和 epilog 代码的信息，请参阅[裸函数调用](../cpp/naked-function-calls.md)。

默认值有关的信息面向 x64 平台，请参阅代码中调用约定[x64 调用约定](../build/x64-calling-convention.md)。 有关在面向 ARM 平台的代码中调用约定问题的信息，请参阅[Visual C++ ARM 迁移的常见问题](../build/common-visual-cpp-arm-migration-issues.md)。

Visual C/C++ 编译器支持下列调用约定。

|关键字|堆栈清理|参数传递|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|调用方|在堆栈上按相反顺序推送参数（从右到左）|
|[__clrcall](../cpp/clrcall.md)|n/a|按顺序将参数加载到 CLR 表达式堆栈上（从左到右）。|
|[__stdcall](../cpp/stdcall.md)|被调用方|在堆栈上按相反顺序推送参数（从右到左）|
|[__fastcall](../cpp/fastcall.md)|被调用方|存储在寄存器中，然后在堆栈上推送|
|[__thiscall](../cpp/thiscall.md)|被调用方|推入堆栈;**this**指针存储在 ECX 中|
|[__vectorcall](../cpp/vectorcall.md)|被调用方|存储在寄存器中，然后按相反顺序在堆栈上推送（从右到左）|

有关相关信息，请参阅[过时的调用约定](../cpp/obsolete-calling-conventions.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[调用约定](../cpp/calling-conventions.md)