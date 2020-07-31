---
title: 引用类型函数返回
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: b2997348a3234302655187af25c9c4644c95e48e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233621"
---
# <a name="reference-type-function-returns"></a>引用类型函数返回

可将函数声明为返回引用类型。 做出此类声明有两个原因：

- 返回的信息是一个返回引用比返回副本更有效的足够大的对象。

- 函数的类型必须为左值。

- 引用的对象在函数返回时不会超出范围。

就像通过引用向函数传递大型对象更有效的方式一样，通过引用*从*函数返回*大型对象也*可能更有效。 引用返回协议使得不必在返回前将对象复制到临时位置。

当函数的计算结果必须为左值时，引用返回类型也可能很有用。 大多数重载运算符属于此类别，尤其是赋值运算符。 重载运算符在[重载运算符](../cpp/operator-overloading.md)中介绍。

## <a name="example"></a>示例

请考虑 `Point` 示例：

```cpp
// refType_function_returns.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

class Point
{
public:
// Define "accessor" functions as
//  reference types.
unsigned& x();
unsigned& y();
private:
// Note that these are declared at class scope:
unsigned obj_x;
unsigned obj_y;
};

unsigned& Point :: x()
{
return obj_x;
}
unsigned& Point :: y()
{
return obj_y;
}

int main()
{
Point ThePoint;
// Use x() and y() as l-values.
ThePoint.x() = 7;
ThePoint.y() = 9;

// Use x() and y() as r-values.
cout << "x = " << ThePoint.x() << "\n"
<< "y = " << ThePoint.y() << "\n";
}
```

## <a name="output"></a>输出

```Output
x = 7
y = 9
```

请注意，函数`x` 和 `y` 被声明为返回引用类型。 这些函数可在赋值语句的每一端上使用。

另请注意在 main 中，ThePoint 对象停留在范围中，因此其引用成员仍处于活动状态，可以安全地访问。

除以下情况之外，引用类型的声明必须包含初始值设定项：

- 显式 **`extern`** 声明

- 类成员的声明

- 类中的声明

- 函数的自变量或函数的返回类型的声明

## <a name="caution-returning-address-of-local"></a>返回局部变量地址时的注意事项

如果在局部范围中声明某个对象，则该对象会在函数返回时销毁。 如果函数返回对该对象的引用，则当调用方尝试使用 null 引用时，该引用可能会在运行时导致访问冲突。

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

在这种情况下，编译器会发出警告： `warning C4172: returning address of local variable or temporary` 。 在简单程序中，如果调用方在覆盖内存位置之前访问引用，则有时可能不会发生访问冲突。 这纯属运气。 请注意该警告。

## <a name="see-also"></a>另请参阅

[参考](../cpp/references-cpp.md)
