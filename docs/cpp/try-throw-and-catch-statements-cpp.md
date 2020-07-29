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
ms.openlocfilehash: 4108d24b2c285b9d55d514dffae7b2efda1b3f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227057"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 语句 (C++)

若要在 c + + 中实现异常处理，请使用 **`try`** 、 **`throw`** 和 **`catch`** 表达式。

首先，使用 **`try`** 块将一个或多个可能引发异常的语句括起来。

**`throw`** 表达式发出信号表示异常情况（通常是错误）已在块中发生 **`try`** 。 您可以使用任何类型的对象作为表达式的操作数 **`throw`** 。 该对象一般用于传达有关错误的信息。 在大多数情况下，我们建议使用[std：： exception](../standard-library/exception-class.md)类或在标准库中定义的一个派生类。 如果其中的类不合适，建议你从 `std::exception` 派生自己的异常类。

若要处理可能引发的异常，请在块后面立即实现一个或多个 **`catch`** 块 **`try`** 。 每个 **`catch`** 块指定它可以处理的异常的类型。

此示例显示了一个 **`try`** 块及其处理程序。 假设 `GetNetworkResource()` 通过网络连接获取数据，并且两个异常类型是从 `std::exception` 派生的用户定义的类。 请注意，异常是通过 **`const`** 语句中的引用捕获的 **`catch`** 。 我们建议你通过值引发异常并通过常数引用将其捕获。

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

子句后的代码 **`try`** 是代码的受保护部分。 **`throw`** 表达式*引发*（即引发）异常。 子句后的代码块 **`catch`** 是异常处理程序。 如果和表达式中的类型兼容，则这是*捕获*引发的异常的处理程序 **`throw`** **`catch`** 。 有关在块中控制类型匹配的规则的列表 **`catch`** ，请参阅[如何计算 Catch 块](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果 **`catch`** 语句指定了省略号（...）而不是类型，则 **`catch`** 块处理每种异常类型。 使用[/eha](../build/reference/eh-exception-handling-model.md)选项进行编译时，它们可能包含 C 结构化异常和系统生成的或应用程序生成的异步异常，如内存保护、被零除和浮点冲突。 因为 **`catch`** 在程序顺序中处理块以查找匹配类型，所以省略号处理程序必须是关联的块的最后一个处理程序 **`try`** 。 请谨慎使用 `catch(...)`；除非 catch 块知道如何处理捕获的特定异常，否则禁止程序继续执行。 `catch(...)` 块一般用于在程序停止执行前记录错误和执行特殊的清理工作。

**`throw`** 没有操作数的表达式会重新引发当前正在处理的异常。 我们建议在重新引发异常时采用该形式，是因为这将保留原始异常的多态类型信息。 此类表达式只应在处理程序中 **`catch`** 或从处理程序中调用的函数中使用 **`catch`** 。 重新引发的异常对象是原始异常对象，而不是副本。

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

[异常和错误处理的新式 c + + 最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[未处理的 c + + 异常](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
