---
title: Catch 块的计算方式 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 027dc87923a588ea891dbf6dd835e2baba75a1cb
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245857"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Catch 块的计算方式 (C++)

虽然通常建议您引发派生自 std::exception 的类型，但 C++ 使您能够引发任何类型的异常。 A C++ exception can be caught by a **catch** handler that specifies the same type as the thrown exception, or by a handler that can catch any type of exception.

如果引发的异常的类型是类，它还具有基类（或类），则它可由接受异常类型的基类和对异常类型的基的引用的处理程序捕获。 请注意，当异常由引用捕获时，会将其绑定到实际引发的异常对象；否则，它将为一个副本（与函数的参数大致相同）。

When an exception is thrown, it may be caught by the following types of **catch** handlers:

- 可以接受任何类型的处理程序（使用省略号语法）。

- A handler that accepts the same type as the exception object; because it is a copy, **const** and **volatile** modifiers are ignored.

- 接受对与异常对象相同的类型的引用的处理程序。

- A handler that accepts a reference to a **const** or **volatile** form of the same type as the exception object.

- A handler that accepts a base class of the same type as the exception object; since it is a copy, **const** and **volatile** modifiers are ignored. The **catch** handler for a base class must not precede the **catch** handler for the derived class.

- 接受对与异常对象相同的类型的基类的引用的处理程序。

- A handler that accepts a reference to a **const** or **volatile** form of a base class of the same type as the exception object.

- 接受可通过标准指针转换规则将引发的指针对象转换为的指针的处理程序。

The order in which **catch** handlers appear is significant, because handlers for a given **try** block are examined in order of their appearance. 例如，将基类的处理程序放置在派生类的处理程序的前面是错误的。 After a matching **catch** handler is found, subsequent handlers are not examined. As a result, an ellipsis **catch** handler must be the last handler for its **try** block. 例如:

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

In this example, the ellipsis **catch** handler is the only handler that is examined.

## <a name="see-also"></a>请参阅

[Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md)