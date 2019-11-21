---
title: Exception handling in MSVC
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
# <a name="exception-handling-in-msvc"></a>Exception handling in MSVC

异常是一个可能超出程序的控制范围的错误条件，它会阻止程序继续沿其常规执行路径执行。 某些操作（包括对象创建、文件输入/输出以及从其他模块中进行的函数调用）都可能是异常的来源，设置在你的程序正常运行时也是如此。 可靠代码可预见并处理异常。 To detect logic errors, use assertions rather than exceptions (see [Using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Kinds of exceptions

The Microsoft C++ compiler (MSVC) supports three kinds of exception handling:

- [C++ exception handling](errors-and-exception-handling-modern-cpp.md)

   对于大多数 C++ 程序，你应使用类型安全的 C++ 异常处理，该处理可确保在堆栈展开过程中调用对象析构函数。

- [Structured exception handling](structured-exception-handling-c-cpp.md)

   Windows 提供其自己的称为 SEH 的异常机制。 建议不要将该机制用于 C++ 或 MFC 编程。 Use SEH only in non-MFC C programs.

- [MFC exceptions](../mfc/exception-handling-in-mfc.md)

Use the [/EH](../build/reference/eh-exception-handling-model.md) compiler option to specify the type of exception handling to use in a project; C++ exception handling is the default. 不要混合错误处理机制；例如，不要将 C++ 异常用于结构化异常处理。 使用 C++ 异常处理可以使你的代码更具可移植性，并且它使你可以处理任何类型的异常。 For more information about the drawbacks of structured exception handling, see [Structured Exception Handling](structured-exception-handling-c-cpp.md). For advice about mixing MFC macros and C++ exceptions, see [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>本节内容

- [Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)

- [How to design for exception safety](how-to-design-for-exception-safety.md)

- [How to interface between exceptional and non-exceptional code](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [The try, catch, and throw Statements](try-throw-and-catch-statements-cpp.md)

- [Catch 块如何计算](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions and Stack Unwinding](exceptions-and-stack-unwinding-in-cpp.md)

- [Exception Specifications](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未处理的 C++ 异常](unhandled-cpp-exceptions.md)

- [混合使用 C（结构化）和 C++ 异常](mixing-c-structured-and-cpp-exceptions.md)

- [Structured Exception Handling (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>请参阅

[C++ 语言参考](cpp-language-reference.md)</br>
[x64 异常处理](../build/exception-handling-x64.md)</br>
[Exception Handling (C++/CLI and C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
