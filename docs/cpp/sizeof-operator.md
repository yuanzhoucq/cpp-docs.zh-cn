---
title: sizeof 运算符
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: c9ae581b1b3bea522f2c1557b8be44ee1f32eef1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032286"
---
# <a name="sizeof-operator"></a>sizeof 运算符

相对于**字符**类型的大小，生成其操作数的大小。

> [!NOTE]
> 有关运算符的信息，`sizeof ...`请参阅[椭圆和可变模板](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>语法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>备注

**大小运算符**的结果为类型`size_t`，在包含文件\<stddef.h>中定义的积分类型。 利用此运算符，你可以避免在程序中指定依赖于计算机的数据大小。

**大小**操作数可以是以下操作数之一：

- 类型名称。 要使用 具有类型名称**的大小**，名称必须包含在括号中。

- 一个表达式。 当与表达式一起使用时，可以使用或没有括号指定**size。** 不计算表达式。

当**sizeof**运算符应用于**字符**类型的对象时，它会产生 1。 当**sizeOF**运算符应用于数组时，它将生成该数组中的字节总数，而不是数组标识符表示的指针的大小。 要获取数组标识符表示的指针的大小，请将其作为参数传递给使用**size 的**函数。 例如：

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

当**sizeof**运算符应用于**类**、**结构**类型或**联合**类型时，结果是该类型对象中的字节数，以及为对齐单词边界上的成员添加的任何填充。 结果不一定对应于通过将各个成员的存储需求相加计算出的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)编译器选项和[包](../preprocessor/pack.md)杂注会影响成员的对齐边界。

即使对于空类，**大小运算符**也永远不会产生 0。

**大小运算符**不能与以下操作数一起使用：

- 函数。 （但是，**大小**可以应用于指向函数的指针。

- 位域。

- 未定义的类。

- 类型**void**。

- 动态分配的数组。

- 外部数组。

- 不完整类型。

- 带括号的不完整类型的名称。

当**sizeOF**运算符应用于引用时，结果与将**sizesize**应用于对象本身的结果相同。

如果大小数组是结构的最后一个元素，**则 sizeof**运算符返回没有数组的结构的大小。

**sizeof**运算符通常用于使用窗体的表达式计算数组中的元素数：

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>请参阅

[具有一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
