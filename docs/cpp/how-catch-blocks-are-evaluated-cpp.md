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
ms.openlocfilehash: 21d68b25fa3695a9b5637dcace081424f99911d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188097"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Catch 块的计算方式 (C++)

虽然通常建议您引发派生自 std::exception 的类型，但 C++ 使您能够引发任何类型的异常。 C + + 异常可以由指定与 **`catch`** 引发的异常相同的类型的处理程序捕获，也可以由可以捕获任何类型的异常的处理程序捕获。

如果引发的异常的类型是类，它还具有基类（或类），则它可由接受异常类型的基类和对异常类型的基的引用的处理程序捕获。 请注意，当异常由引用捕获时，会将其绑定到实际引发的异常对象；否则，它将为一个副本（与函数的参数大致相同）。

当引发异常时，它可能由以下类型的 **`catch`** 处理程序捕获：

- 可以接受任何类型的处理程序（使用省略号语法）。

- 接受与异常对象相同的类型的处理程序;由于它是副本，因此 **`const`** **`volatile`** 忽略修饰符。

- 接受对与异常对象相同的类型的引用的处理程序。

- 接受对与 **`const`** **`volatile`** 异常对象类型相同的类型的引用的处理程序。

- 接受与异常对象类型相同的基类的处理程序;由于它是副本， **`const`** 因此 **`volatile`** 忽略修饰符。 **`catch`** 基类的处理程序不能位于 **`catch`** 派生类的处理程序之前。

- 接受对与异常对象相同的类型的基类的引用的处理程序。

- 接受对与 **`const`** 异常对象相同的类型的基类的引用的处理程序 **`volatile`** 。

- 接受可通过标准指针转换规则将引发的指针对象转换为的指针的处理程序。

**`catch`** 处理程序的显示顺序非常重要，因为给定块的处理程序 **`try`** 按其外观的顺序进行检查。 例如，将基类的处理程序放置在派生类的处理程序的前面是错误的。   找到匹配的 **`catch`** 处理程序后，不会检查后续处理程序。 因此，省略号 **`catch`** 处理程序必须是其块的最后一个处理程序 **`try`** 。 例如：

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

在此示例中，省略号 **`catch`** 处理程序是唯一检查的处理程序。

## <a name="see-also"></a>另请参阅

[异常和错误处理的新式 c + + 最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)
