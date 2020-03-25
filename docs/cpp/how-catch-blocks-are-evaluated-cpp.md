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
ms.openlocfilehash: 11804c48631659b84006abb824837efea3902416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188632"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Catch 块的计算方式 (C++)

虽然通常建议您引发派生自 std::exception 的类型，但 C++ 使您能够引发任何类型的异常。 C++异常可由指定与引发的异常相同的类型的**catch**处理程序捕获，或由可以捕获任何类型的异常的处理程序捕获。

如果引发的异常的类型是类，它还具有基类（或类），则它可由接受异常类型的基类和对异常类型的基的引用的处理程序捕获。 请注意，当异常由引用捕获时，会将其绑定到实际引发的异常对象；否则，它将为一个副本（与函数的参数大致相同）。

当引发异常时，它可能由以下类型的**catch**处理程序捕获：

- 可以接受任何类型的处理程序（使用省略号语法）。

- 接受与异常对象相同的类型的处理程序;由于它是副本，因此将忽略**const**和**volatile**修饰符。

- 接受对与异常对象相同的类型的引用的处理程序。

- 接受对与异常对象类型相同的**const**或**volatile**形式的引用的处理程序。

- 接受与异常对象类型相同的基类的处理程序;由于它是副本，因此**const**和**volatile**修饰符将被忽略。 基类的**catch**处理程序不能位于派生类的**catch**处理程序之前。

- 接受对与异常对象相同的类型的基类的引用的处理程序。

- 接受对与异常对象类型相同的基类的**const**或**volatile**形式的引用的处理程序。

- 接受可通过标准指针转换规则将引发的指针对象转换为的指针的处理程序。

**Catch**处理程序的显示顺序非常重要，因为给定**try**块的处理程序按其外观的顺序进行检查。 例如，将基类的处理程序放置在派生类的处理程序的前面是错误的。 找到匹配的**catch**处理程序后，不会检查后续处理程序。 因此，省略号**catch**处理程序必须是其**try**块的最后一个处理程序。 例如：

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

在此示例中，省略号**catch**处理程序是唯一检查的处理程序。

## <a name="see-also"></a>另请参阅

[异常C++和错误处理的新式最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)
