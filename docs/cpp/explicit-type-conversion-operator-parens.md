---
title: 显式类型转换运算符：()
ms.date: 11/04/2016
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
ms.openlocfilehash: c168653a82b4d4c5023de1f76a1e6269625c74d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354864"
---
# <a name="explicit-type-conversion-operator-"></a>显式类型转换运算符：()

C++ 允许使用与函数调用语法类似的语法进行显式类型转换。

## <a name="syntax"></a>语法

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>备注

*简单类型名称*后跟括号中包含的*表达式列表*使用指定的表达式构造指定类型的对象。 以下示例显示到类型 int 的显式类型转换：

```cpp
int i = int( d );
```

下面的示例显示了一个`Point`类。

## <a name="example"></a>示例

```cpp
// expre_Explicit_Type_Conversion_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
public:
    // Define default constructor.
    Point() { _x = _y = 0; }
    // Define another constructor.
    Point( int X, int Y ) { _x = X; _y = Y; }

    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
    void Show()   { cout << "x = " << _x << ", "
                         << "y = " << _y << "\n"; }
private:
    unsigned _x;
    unsigned _y;
};

int main()
{
    Point Point1, Point2;

    // Assign Point1 the explicit conversion
    //  of ( 10, 10 ).
    Point1 = Point( 10, 10 );

    // Use x() as an l-value by assigning an explicit
    //  conversion of 20 to type unsigned.
    Point1.x() = unsigned( 20 );
    Point1.Show();

    // Assign Point2 the default Point object.
    Point2 = Point();
    Point2.Show();
}
```

## <a name="output"></a>输出

```Output
x = 20, y = 10
x = 0, y = 0
```

尽管前面的示例演示了使用常量的显式类型转换，但在对对象执行转换时，此方法也同样有效。 以下代码片段对此进行了演示：

```cpp
int i = 7;
float d;

d = float( i );
```

还可以使用“cast”语法指定显式类型转换。 使用 cast 语法重写的上一个示例是：

```cpp
d = (float)i;
```

当从单个值转换时，强制转换和函数样式转换都有相同的结果。 但是，在函数样式语法中，可以为转换指定多个自变量。 此差异对用户定义的类型非常重要。 请考虑 `Point` 类及其转换：

```cpp
struct Point
{
    Point( short x, short y ) { _x = x; _y = y; }
    ...
    short _x, _y;
};
...
Point pt = Point( 3, 10 );
```

前面的示例使用函数样式转换，演示如何将两个值（一个用于*x*和一个用于*y）* 转换为用户定义的类型`Point`。

> [!CAUTION]
> 请谨慎使用显式类型转换，因其会重写 C++ 编译器的内置类型检查。

[强制转换](../cpp/cast-operator-parens.md)记号必须用于转换为没有*简单类型名称*的类型（例如指针或引用类型）。 转换为可以使用*简单类型名称*表示的类型可以以任一形式编写。

在强制转换中的类型定义是非法的。

## <a name="see-also"></a>另请参阅

[后修复表达式](../cpp/postfix-expressions.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
