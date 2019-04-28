---
title: sizeof 运算符
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 9edd6420193fbc1ff6013c545b294851ce105848
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267214"
---
# <a name="sizeof-operator"></a>sizeof 运算符

生成其操作数的类型大小的大小**char**。

> [!NOTE]
>  璝惠`sizeof ...`运算符，请参阅[省略号和可变参数模板](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>语法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>备注

结果**sizeof**运算符的类型是`size_t`，在包含文件中定义的整数类型\<stddef.h >。 利用此运算符，你可以避免在程序中指定依赖于计算机的数据大小。

到操作数**sizeof**可以是以下之一：

- 类型名称。 若要使用**sizeof**使用类型名称，名称必须括在括号中。

- 一个表达式。 与表达式一起使用时**sizeof**可以使用或不带括号指定。 不计算表达式。

当**sizeof**运算符应用于类型的对象**char**，它将生成 1。 当**sizeof**运算符应用到一个数组，它将产生不是由数组标识符表示的指针的大小、 该数组中的字节总数。 若要获取由数组标识符表示的指针的大小，它将作为参数传递到使用的函数**sizeof**。 例如：

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

当**sizeof**运算符应用于**类**，**结构**，或者**联合**类型，结果是该对象中的字节数类型和添加以单词边界上对齐成员的任何填充。 结果不一定对应于通过将各个成员的存储需求相加计算出的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)编译器选项和[pack](../preprocessor/pack.md)杂注影响成员的对齐边界。

**Sizeof**运算符永远不会产生 0，即使对于空类。

**Sizeof**运算符不能与以下操作数一起使用：

- 函数。 (但是， **sizeof**可以应用于指向函数的指针。)

- 位域。

- 未定义的类。

- 类型**void**。

- 动态分配的数组。

- 外部数组。

- 不完整类型。

- 带括号的不完整类型的名称。

当**sizeof**运算符应用于引用，则结果为相同像**sizeof**应用到对象本身。

如果未确定大小的数组是一个结构，最后一个元素**sizeof**运算符将返回不带数组结构的大小。

**Sizeof**运算符通常用于计算数组中使用形式的表达式中的元素数：

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)