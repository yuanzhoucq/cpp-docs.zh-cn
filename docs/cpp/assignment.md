---
title: 分配
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: f1697a8de3dff6c46de01db6bbff5447c03b6282
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190698"
---
# <a name="assignment"></a>分配

赋值运算符（ **=** ）严格地说是二元运算符。 其声明与任何其他二元运算符的相同，但有以下例外：

- 它必须是非静态成员函数。 不能将**operator =** 声明为非成员函数。
- 它不由派生类继承。
- 如果类类型不存在，则编译器会为类类型生成默认的**operator =** 函数。

以下示例阐释如何声明赋值运算符：

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

提供的参数是表达式的右侧。 此运算符返回对象以保留赋值运算符的行为，赋值运算符在赋值完成后返回左侧的值。 这允许链接分配，如：

```cpp
pt1 = pt2 = pt3;
```

复制赋值运算符不会与复制构造函数混淆。 在从现有对象构造新对象的过程中调用后者：

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> 建议遵循[三个规则](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))：定义复制赋值运算符的类还应显式定义复制构造函数、析构函数和，从 c + + 11 开始，移动构造函数和移动赋值运算符。

## <a name="see-also"></a>另请参阅

- [运算符重载](../cpp/operator-overloading.md)
- [复制构造函数和复制赋值运算符 (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
