---
title: 递增和递减运算符重载 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 8d64f0af994f88d0f4ecd3a5921de4a16b8bdaaa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178277"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>递增和递减运算符重载 (C++)

由于递增和递减运算符各有两个变量，因此它们属于一个特殊类别：

- 前置递增和后置递增

- 前置递减和后置递减

编写重载的运算符函数时，为这些运算符的前缀和后缀版本实现单独的版本很有用。 若要区分这两者，请遵循以下规则：运算符的前缀形式与任何其他一元运算符的声明方式完全相同;后缀形式接受**int**类型的其他参数。

> [!NOTE]
>  为递增或递减运算符的后缀形式指定重载运算符时，附加自变量的类型必须为**int**;指定任何其他类型将生成错误。

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

表示递增或递减运算符的后缀形式的**int**类型的参数通常不用于传递参数。 它通常包含值 0。 但是，可按以下方式使用它：

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
