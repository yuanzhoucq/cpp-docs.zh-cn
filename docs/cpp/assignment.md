---
title: 分配 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05f88eaaef32c509b400441830b5dcc311bf6769
ms.sourcegitcommit: 7127467af82147657d0fd7a41fe9c633c4a8453c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "43054010"
---
# <a name="assignment"></a>赋值

赋值运算符 (**=**) 严格地说，是二元运算符。 其声明与任何其他二元运算符的相同，但有以下例外：

- 它必须是非静态成员函数。 否**运算符 =** 可以声明为非成员函数。
- 它不由派生类继承。
- 默认值**运算符 =** 对于类类型，编译器可以生成函数，如果不存在。

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

提供的自变量是表达式的右侧。 此运算符返回对象以保留赋值运算符的行为，赋值运算符在赋值完成后返回左侧的值。 这允许链接的分配，如：

```cpp
pt1 = pt2 = pt3;
```

复制赋值运算符是不与复制构造函数相混淆。 从一个现有方式后者调用新的对象构造期间：

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is line is similar to the following:
Point pt4(pt1); // Copy constructor call
```

> [!NOTE]
> 最好按照[三个规则](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))，用于定义复制赋值运算符的类应显式定义的复制构造函数，析构函数，然后，使用启动 C + + 11，移动构造函数和移动赋值运算符。

## <a name="see-also"></a>请参阅

- [运算符重载](../cpp/operator-overloading.md)
- [复制构造函数和复制赋值运算符 (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)