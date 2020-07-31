---
title: 递增和递减运算符重载 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 10cda57b74a7da57f2d48b91854b5d37c8d181f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186979"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>递增和递减运算符重载 (C++)

由于递增和递减运算符各有两个变量，因此它们属于一个特殊类别：

- 前置递增和后置递增

- 前置递减和后置递减

编写重载的运算符函数时，为这些运算符的前缀和后缀版本实现单独的版本很有用。 若要区分这两者，请遵循以下规则：运算符的前缀形式与任何其他一元运算符的声明方式完全相同;后缀形式接受类型的其他参数 **`int`** 。

> [!NOTE]
> 为递增或递减运算符的后缀形式指定重载运算符时，附加参数必须是类型 **`int`** ; 指定任何其他类型将生成错误。

以下示例显示如何为 `Point` 类定义前缀和后缀递增和递减运算符：

```cpp
// increment_and_decrement1.cpp
class Point
{
public:
   // Declare prefix and postfix increment operators.
   Point& operator++();       // Prefix increment operator.
   Point operator++(int);     // Postfix increment operator.

   // Declare prefix and postfix decrement operators.
   Point& operator--();       // Prefix decrement operator.
   Point operator--(int);     // Postfix decrement operator.

   // Define default constructor.
   Point() { _x = _y = 0; }

   // Define accessor functions.
   int x() { return _x; }
   int y() { return _y; }
private:
   int _x, _y;
};

// Define prefix increment operator.
Point& Point::operator++()
{
   _x++;
   _y++;
   return *this;
}

// Define postfix increment operator.
Point Point::operator++(int)
{
   Point temp = *this;
   ++*this;
   return temp;
}

// Define prefix decrement operator.
Point& Point::operator--()
{
   _x--;
   _y--;
   return *this;
}

// Define postfix decrement operator.
Point Point::operator--(int)
{
   Point temp = *this;
   --*this;
   return temp;
}
int main()
{
}
```

可使用以下函数头在文件范围中（全局）定义同一运算符：

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

**`int`** 表示递增或递减运算符的后缀形式的类型的参数通常不用于传递参数。 它通常包含值 0。 但是，可按以下方式使用它：

```cpp
// increment_and_decrement2.cpp
class Int
{
public:
    Int &operator++( int n );
private:
    int _i;
};

Int& Int::operator++( int n )
{
    if( n != 0 )    // Handle case where an argument is passed.
        _i += n;
    else
        _i++;       // Handle case where no argument is passed.
    return *this;
}
int main()
{
   Int i;
   i.operator++( 25 ); // Increment by 25.
}
```

除显式调用之外，没有针对使用递增或递减运算符来传递这些值的语法，如前面的代码所示。 实现此功能的一种更简单的方法是重载加法/赋值运算符（ **+=** ）。

## <a name="see-also"></a>另请参阅

[运算符重载](../cpp/operator-overloading.md)
