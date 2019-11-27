---
title: MSVC 中的异常处理
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246592"
---
# <a name="exception-handling-in-msvc"></a>MSVC 中的异常处理

异常是一个可能超出程序的控制范围的错误条件，它会阻止程序继续沿其常规执行路径执行。 某些操作（包括对象创建、文件输入/输出以及从其他模块中进行的函数调用）都可能是异常的来源，设置在你的程序正常运行时也是如此。 可靠代码可预见并处理异常。 若要检测逻辑错误，请使用断言而不是异常（请参阅[使用断言](/visualstudio/debugger/c-cpp-assertions)）。

## <a name="kinds-of-exceptions"></a>异常类型

Microsoft C++编译器（MSVC）支持以下三种异常处理：

- [C++异常处理](errors-and-exception-handling-modern-cpp.md)

   对于大多数 C++ 程序，你应使用类型安全的 C++ 异常处理，该处理可确保在堆栈展开过程中调用对象析构函数。

- [结构化异常处理](structured-exception-handling-c-cpp.md)

   Windows 提供其自己的称为 SEH 的异常机制。 建议不要将该机制用于 C++ 或 MFC 编程。 仅在非 MFC C 程序中使用 SEH。

- [MFC 异常](../mfc/exception-handling-in-mfc.md)

使用[/EH](../build/reference/eh-exception-handling-model.md)编译器选项可指定要在项目中使用的异常处理类型;C++默认情况下，异常处理。 不要混合错误处理机制；例如，不要将 C++ 异常用于结构化异常处理。 使用 C++ 异常处理可以使你的代码更具可移植性，并且它使你可以处理任何类型的异常。 有关结构化异常处理的缺点的详细信息，请参阅[结构化异常处理](structured-exception-handling-c-cpp.md)。 有关混合 MFC 宏和C++异常的建议，请参阅[异常：使用 MFC 宏C++和异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

## <a name="in-this-section"></a>本节内容

- [异常C++和错误处理的新式最佳实践](errors-and-exception-handling-modern-cpp.md)

- [如何设计异常安全](how-to-design-for-exception-safety.md)

- [如何在异常和非异常代码之间进行交互](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Try、catch 和 throw 语句](try-throw-and-catch-statements-cpp.md)

- [Catch 块如何计算](how-catch-blocks-are-evaluated-cpp.md)

- [异常和堆栈展开](exceptions-and-stack-unwinding-in-cpp.md)

- [异常规范](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未处理的 C++ 异常](unhandled-cpp-exceptions.md)

- [混合使用 C（结构化）和 C++ 异常](mixing-c-structured-and-cpp-exceptions.md)

- [结构化异常处理（SEH）（CC++/）](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>另请参阅

[C++ 语言参考](cpp-language-reference.md)</br>
[x64 异常处理](../build/exception-handling-x64.md)</br>
[异常处理（C++/Cli 和C++/cx）](../extensions/exception-handling-cpp-component-extensions.md)
