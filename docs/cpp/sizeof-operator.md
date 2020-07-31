---
title: sizeof 运算符
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 13e181bf84e359d433fbe951b1aa69320a1f0013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186290"
---
# <a name="sizeof-operator"></a>sizeof 运算符

根据类型的大小生成操作数的大小 **`char`** 。

> [!NOTE]
> 有关运算符的信息 `sizeof ...` ，请参阅[省略号和可变参数模板](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>语法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>备注

运算符的结果 **`sizeof`** 为类型，它是 `size_t` 在包含文件中定义的整型类型 \<stddef.h> 。 利用此运算符，你可以避免在程序中指定依赖于计算机的数据大小。

的操作数 **`sizeof`** 可以是下列其中一项：

- 类型名称。 若要将 **`sizeof`** 与类型名称一起使用，必须将名称括在括号中。

- 一个表达式。 与表达式一起使用时， **`sizeof`** 可以使用或不带括号来指定。 不计算表达式。

将 **`sizeof`** 运算符应用于类型的对象时，将 **`char`** 生成1。 将 **`sizeof`** 运算符应用于数组时，它将生成该数组中的总字节数，而不是由数组标识符表示的指针的大小。 若要获取由数组标识符表示的指针的大小，请将其作为参数传递给使用的函数 **`sizeof`** 。 例如：

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

将 **`sizeof`** 运算符应用于 **`class`** 、 **`struct`** 或 **`union`** 类型时，结果为该类型的对象中的字节数，加上为对齐 word 边界上的成员而添加的任何填充。 结果不一定对应于通过将各个成员的存储需求相加计算出的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)编译器选项和[pack](../preprocessor/pack.md)杂注影响成员的对齐边界。

**`sizeof`** 运算符永远不会产生0，即使对于空类也是如此。

**`sizeof`** 运算符不能与以下操作数一起使用：

- 函数。 （但是， **`sizeof`** 可应用到指向函数的指针。）

- 位域。

- 未定义的类。

- 类型 **`void`** 。

- 动态分配的数组。

- 外部数组。

- 不完整类型。

- 带括号的不完整类型的名称。

将 **`sizeof`** 运算符应用于引用时，结果与应用于对象本身的结果相同 **`sizeof`** 。

如果成员列表数组数组是结构的最后一个元素，则运算符将 **`sizeof`** 返回不带数组的结构的大小。

**`sizeof`** 运算符通常用于计算数组中使用以下形式的表达式的元素数：

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
