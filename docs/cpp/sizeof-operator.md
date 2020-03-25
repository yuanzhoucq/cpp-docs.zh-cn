---
title: sizeof 运算符
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: bc1165cf1df3933575013906d1b24673467f0b36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178712"
---
# <a name="sizeof-operator"></a>sizeof 运算符

根据**char**类型的大小生成操作数的大小。

> [!NOTE]
>  有关 `sizeof ...` 运算符的信息，请参阅[省略号和可变参数模板](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>语法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>备注

**Sizeof**运算符的结果为类型 `size_t`，在包含文件 \<stddef.h > 中定义的整数类型。 利用此运算符，你可以避免在程序中指定依赖于计算机的数据大小。

**Sizeof**的操作数可以是下列项之一：

- 类型名称。 若要将**sizeof**用于类型名称，则必须将该名称括在括号中。

- 一个表达式。 与表达式一起使用时，可以使用或不使用括号来指定**sizeof** 。 不计算表达式。

当**sizeof**运算符应用于**char**类型的对象时，它将生成1。 当**sizeof**运算符应用于数组时，它将生成该数组中的总字节数，而不是由数组标识符表示的指针的大小。 若要获取由数组标识符表示的指针的大小，请将其作为参数传递给使用**sizeof**的函数。 例如：

## <a name="example"></a>示例

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>示例输出

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

当**sizeof**运算符应用于**类**、**结构**或**联合**类型时，结果为该类型的对象中的字节数，加上为对齐 word 边界上的成员而添加的任何填充。 结果不一定对应于通过将各个成员的存储需求相加计算出的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)编译器选项和[pack](../preprocessor/pack.md)杂注影响成员的对齐边界。

**Sizeof**运算符从不产生0，即使对于空类也是如此。

**Sizeof**运算符不能与以下操作数一起使用：

- 函数。 （但是，可以将**sizeof**应用到指向函数的指针。）

- 位域。

- 未定义的类。

- 类型**void**。

- 动态分配的数组。

- 外部数组。

- 不完整类型。

- 带括号的不完整类型的名称。

当**sizeof**运算符应用于引用时，结果将与将**sizeof**应用于对象本身相同。

如果成员列表数组数组是结构的最后一个元素，则**sizeof**运算符将返回不带数组的结构的大小。

**Sizeof**运算符通常用于计算数组中使用以下形式的表达式的元素数：

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>另请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
