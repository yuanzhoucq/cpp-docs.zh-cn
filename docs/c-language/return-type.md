---
title: 返回类型
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 1d905e02be02784b562b9d1a8f72a9bfa4057b9b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226322"
---
# <a name="return-type"></a>返回类型

函数的返回类型建立由该函数返回的值的大小和类型，并与以下语法中的 type-specifier 相对应：

## <a name="syntax"></a>语法

function-definition  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* is Microsoft-specific \*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`__int8` /\* 特定于 Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`__int16` /\* 特定于 Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`__int32` /\* 特定于 Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`__int64` /\* 特定于 Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

type-specifier  可以指定任何基本、结构或联合类型。 如果不包括 type-specifier，则假定返回类型为 `int`。

函数定义中给定的返回类型必须与程序中其他位置的函数声明中的返回类型相匹配。 当执行包含表达式的 `return` 语句时，函数返回值。 计算该表达式，转换为返回值类型（如果需要）并返回到调用函数的点。 如果函数是使用返回类型 `void` 进行声明，则包含表达式的返回语句会生成警告，并且表达式不会被计算。

以下示例阐释函数返回值。

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

此示例使用 `typedef` 声明定义了 `STUDENT` 类型，并将函数 `sortstu` 定义为包含 `STUDENT` 返回类型。 函数选择并返回其两个结构参数之一。 在对函数的后续调用中，编译器会检查以确保参数类型是 `STUDENT`。

> [!NOTE]
> 通过传递指向结构的指针而不是整个结构来提高效率。

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

此示例定义了一个返回指向字符数组的指针的函数。 该函数采用两个字符数组（字符串）作为参数，并返回指向两个字符串中较短的一个字符串的指针。 指向数组的指针指向数组中的第一个元素，并具有其类型；因此，函数的返回类型是指向类型 `char` 的指针。

在调用函数之前，不需要使用 `int` 返回类型来声明函数，但建议使用原型，以便启用对参数和返回值的正确类型检查。

## <a name="see-also"></a>请参阅

[C 函数定义](../c-language/c-function-definitions.md)
