---
title: MSVC 中的异常处理
description: C++语言引用异常处理概述。
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396272"
---
# <a name="exception-handling-in-msvc"></a>MSVC 中的异常处理

异常是一个可能超出程序的控制范围的错误条件，它会阻止程序继续沿其常规执行路径执行。 某些操作（包括对象创建、文件输入/输出和从其他模块进行的函数调用）都是异常的潜在来源，即使程序运行正确也是如此。 可靠代码可预见并处理异常。 要检测逻辑错误，请使用断言而不是异常（请参阅[使用断言](/visualstudio/debugger/c-cpp-assertions)）。

## <a name="kinds-of-exceptions"></a>异常类型

Microsoft C++编译器 （MSVC） 支持三种异常处理：

- [C++异常处理](errors-and-exception-handling-modern-cpp.md)

   对于大多数C++程序，应使用C++异常处理。 它是类型安全的，并确保在堆栈展开期间调用对象析构函数。

- [结构化异常处理](structured-exception-handling-c-cpp.md)

   Windows 提供其自己的异常机制，称为结构化异常处理 （SEH）。 不建议用于C++或 MFC 编程。 仅在非 MFC C 程序中使用 SEH。

- [MFC 异常](../mfc/exception-handling-in-mfc.md)

   自版本 3.0 以来，MFC 一直使用C++异常。 它仍然支持其较旧的异常处理宏，这些宏类似于窗体中C++异常。 有关混合 MFC 宏和C++异常的建议，请参阅[例外：使用 MFC 宏和C++异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

使用[/EH](../build/reference/eh-exception-handling-model.md)编译器选项指定要在C++项目中使用的异常处理模型。 标准C++异常处理 （**/EHsc**） 是 Visual Studio 中新C++项目中的默认值。

我们不建议您混合异常处理机制。 例如，不要使用C++异常进行结构化异常处理。 使用C++异常处理独占功能可使代码更加便于使用，并且允许您处理任何类型的异常。 有关结构化异常处理的缺点的详细信息，请参阅[结构化异常处理](structured-exception-handling-c-cpp.md)。

## <a name="in-this-section"></a>在本节中

- [用于异常和错误处理的现代C++最佳实践](errors-and-exception-handling-modern-cpp.md)

- [如何设计异常安全](how-to-design-for-exception-safety.md)

- [如何在特殊代码和非特殊代码之间接口](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [try、catch 和 throw 语句](try-throw-and-catch-statements-cpp.md)

- [如何评估 Catch 块](how-catch-blocks-are-evaluated-cpp.md)

- [异常和堆栈展开](exceptions-and-stack-unwinding-in-cpp.md)

- [异常规格](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未处理C++异常](unhandled-cpp-exceptions.md)

- [混合 C（结构化）和C++例外](mixing-c-structured-and-cpp-exceptions.md)

- [结构化异常处理 (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>另请参阅

[C++语言参考](cpp-language-reference.md)</br>
[x64 异常处理](../build/exception-handling-x64.md)</br>
[异常处理（C++/CLI 和C++/CX）](../extensions/exception-handling-cpp-component-extensions.md)
