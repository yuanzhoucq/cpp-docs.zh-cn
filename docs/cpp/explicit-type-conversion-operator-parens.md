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
ms.openlocfilehash: 9dc9440db9ea1ff7285ff9b682f6be9900c2a1ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527694"
---
# <a name="explicit-type-conversion-operator-"></a>显式类型转换运算符：()

C++ 允许使用与函数调用语法类似的语法进行显式类型转换。

## <a name="syntax"></a>语法

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>备注

一个*简单类型名称*跟*表达式列表*括在括号构造使用指定的表达式的指定类型的对象。 以下示例显示到类型 int 的显式类型转换：

```cpp
int i = int( d );
```

下面的示例演示`Point`类。

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

当从单个值转换时，强制转换和函数样式转换都有相同的结果。 但是，在函数样式语法中，可以为转换指定多个参数。 此差异对用户定义的类型非常重要。 请考虑 `Point` 类及其转换：

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

上述示例中，使用函数样式转换，演示如何将两个值 (一个用于*x* ，另一个用于*y*) 为用户定义类型`Point`。

> [!CAUTION]
>  请谨慎使用显式类型转换，因其会重写 C++ 编译器的内置类型检查。

[Cast](../cpp/cast-operator-parens.md)表示法必须用于转换为类型，不具有*简单类型名称*（指针或引用类型，例如）。 可以使用表示的类型转换*简单类型名称*可以采用两种形式编写。

在强制转换中的类型定义是非法的。

## <a name="see-also"></a>请参阅

[后缀表达式](../cpp/postfix-expressions.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)