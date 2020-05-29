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
ms.openlocfilehash: 03f7f6f5a1a2842ad7fb0ba2715fada130277e70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187981"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 语句 (C++)

若C++要在中实现异常处理，请使用**try**、 **throw**和**catch**表达式。

首先，使用**try**块将一个或多个可能引发异常的语句括起来。

**Throw**表达式发出信号，指示在**try**块中发生了异常情况（通常是错误）。 您可以使用任何类型的对象作为**throw**表达式的操作数。 该对象一般用于传达有关错误的信息。 在大多数情况下，我们建议使用[std：： exception](../standard-library/exception-class.md)类或在标准库中定义的一个派生类。 如果其中的类不合适，建议你从 `std::exception` 派生自己的异常类。

若要处理可能引发的异常，请在**try**块后面立即实现一个或多个**catch**块。 每个**catch**块指定它可以处理的异常的类型。

此示例演示了**try**块及其处理程序。 假设 `GetNetworkResource()` 通过网络连接获取数据，并且两个异常类型是从 `std::exception` 派生的用户定义的类。 请注意，在**catch**语句中，异常是由**const** reference 捕获的。 我们建议你通过值引发异常并通过常数引用将其捕获。

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

**Try**子句后的代码是代码的受保护部分。 **引发***表达式引发（即*引发）异常。 **Catch**子句后的代码块是异常处理程序。 如果**throw**和**catch**表达式中的类型兼容，则这是*捕获*引发的异常的处理程序。 有关控制**catch**块中的类型匹配的规则的列表，请参阅[如何计算 catch 块](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果**catch**语句指定了一个省略号（...）而不是类型，则**catch**块处理每个异常类型。 使用[/eha](../build/reference/eh-exception-handling-model.md)选项进行编译时，它们可能包含 C 结构化异常和系统生成的或应用程序生成的异步异常，如内存保护、被零除和浮点冲突。 因为在程序顺序中处理**catch**块以查找匹配类型，所以省略号处理程序必须是关联的**try**块的最后一个处理程序。 请谨慎使用 `catch(...)`；除非 catch 块知道如何处理捕获的特定异常，否则禁止程序继续执行。 `catch(...)` 块一般用于在程序停止执行前记录错误和执行特殊的清理工作。

没有操作数的**throw**表达式会重新引发当前正在处理的异常。 我们建议在重新引发异常时采用该形式，是因为这将保留原始异常的多态类型信息。 此类表达式只应在**catch**处理程序或从**catch**处理程序调用的函数中使用。 重新引发的异常对象是原始异常对象，而不是副本。

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

## <a name="see-also"></a>另请参阅

[异常C++和错误处理的新式最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[未处理的 C++ 异常](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
