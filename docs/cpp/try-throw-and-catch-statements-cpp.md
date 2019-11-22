---
title: try、throw 和 catch 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 31ed5f7a17b9b45dbbecf5ccb29d2b51a7635eaa
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245145"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 语句 (C++)

To implement exception handling in C++, you use **try**, **throw**, and **catch** expressions.

First, use a **try** block to enclose one or more statements that might throw an exception.

A **throw** expression signals that an exceptional condition—often, an error—has occurred in a **try** block. You can use an object of any type as the operand of a **throw** expression. 该对象一般用于传达有关错误的信息。 In most cases, we recommend that you use the [std::exception](../standard-library/exception-class.md) class or one of the derived classes that are defined in the standard library. 如果其中的类不合适，建议你从 `std::exception` 派生自己的异常类。

To handle exceptions that may be thrown, implement one or more **catch** blocks immediately following a **try** block. Each **catch** block specifies the type of exception it can handle.

This example shows a **try** block and its handlers. 假设 `GetNetworkResource()` 通过网络连接获取数据，并且两个异常类型是从 `std::exception` 派生的用户定义的类。 Notice that the exceptions are caught by **const** reference in the **catch** statement. 我们建议你通过值引发异常并通过常数引用将其捕获。

## <a name="example"></a>示例

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>备注

The code after the **try** clause is the guarded section of code. The **throw** expression *throws*—that is, raises—an exception. The code block after the **catch** clause is the exception handler. This is the handler that *catches* the exception that's thrown if the types in the **throw** and **catch** expressions are compatible. For a list of rules that govern type-matching in **catch** blocks, see [How Catch Blocks are Evaluated](../cpp/how-catch-blocks-are-evaluated-cpp.md). If the **catch** statement specifies an ellipsis (...) instead of a type, the **catch** block handles every type of exception. When you compile with the [/EHa](../build/reference/eh-exception-handling-model.md) option, these can include C structured exceptions and system-generated or application-generated asynchronous exceptions such as memory protection, divide-by-zero, and floating-point violations. Because **catch** blocks are processed in program order to find a matching type, an ellipsis handler must be the last handler for the associated **try** block. 请谨慎使用 `catch(...)`；除非 catch 块知道如何处理捕获的特定异常，否则禁止程序继续执行。 `catch(...)` 块一般用于在程序停止执行前记录错误和执行特殊的清理工作。

A **throw** expression that has no operand re-throws the exception currently being handled. 我们建议在重新引发异常时采用该形式，是因为这将保留原始异常的多态类型信息。 Such an expression should only be used in a **catch** handler or in a function that's called from a **catch** handler. 重新引发的异常对象是原始异常对象，而不是副本。

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>请参阅

[Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[未处理的 C++ 异常](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)