---
title: switch语句（c + +）
description: Microsoft Visual Studio c + + 中对标准 c + + 语句的引用 switch 。
ms.date: 04/25/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "83389696"
---
# <a name="switch-statement-c"></a>`switch`语句（c + +）

允许根据整型表达式的值在多个代码段中进行选择。

## <a name="syntax"></a>语法

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub><sup>C + + 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>备注

`switch` 语句使控件根据 `condition` 的值转移到其语句正文中的一个 `labeled-statement`  。

*`condition`* 必须具有整型类型，或者是具有到整型的明确转换的类类型。 整数提升的发生方式如[标准转换](standard-conversions.md)中所述。

__`switch`__ 语句体包含一系列 __`case`__ 标签和一个可选 __`default`__ 标签。 *`labeled-statement`* 是以下标签和后面的语句之一。 带标签的语句无语法要求，但如果 __`switch`__ 没有这些语句，语句就毫无意义了。 语句中的两个 *`constant-expression`* 值的 __`case`__ 计算结果不能为相同的值。 __`default`__ 标签只能出现一次。 __`default`__ 语句通常放置在末尾，但它可以出现在语句体中的任何位置 __`switch`__ 。 `case` 或 `default` 标签只能显示在 `switch` 语句内部    。

*`constant-expression`* 每个标签中的 __`case`__ 会转换为与相同类型的常数值 *`condition`* 。 然后，比较与是否 *`condition`* 相等。 控件将传递到值后的第一条语句 __`case`__ *`constant-expression`* *`condition`* 。 下表中显示了生成的行为。

### <a name="switch-statement-behavior"></a>`switch`语句行为

| 条件 | 操作 |
|--|--|
| 转换后的值与提升的控制表达式的值匹配。 | 控制将转移到跟在该标签后面的语句。 |
| 没有常量与标签中的常量匹配 __`case`__ ; 有一个 __`default`__ 标签。 | 控制将转移到 __`default`__ 标签。 |
| 没有常量与标签中的常量匹配 __`case`__ ; 不存在任何 __`default`__ 标签。 | 控制在语句后传递到语句 __`switch`__ 。 |

如果找到匹配的表达式，则执行可以继续，稍后 __`case`__ 或 __`default`__ 标签。 [`break`](../cpp/break-statement-cpp.md)语句用于停止执行并将控制转移到语句后面的语句 __`switch`__ 。 如果没有 __`break`__ 语句，则将执行从匹配的标签到末尾的每个语句 __`case`__ __`switch`__ ，包括 __`default`__ 。 例如：

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

在上面的示例中，如果 `uppercase_A` 是大写 `c`，则 `'A'` 将递增。 __`break`__ 后的语句 `uppercase_A++` 终止了 __`switch`__ 语句体的执行，并将控制权传递到 __`while`__ 循环。 如果没有 __`break`__ 语句，执行将 "贯穿" 到下一个标记语句，因此 `lowercase_a` 和也将 `other` 递增。 的语句将提供类似的目的 __`break`__ `case 'a'` 。 如果 `c` 是小写 `'a'` ， `lowercase_a` 则递增，语句将 __`break`__ 终止 __`switch`__ 语句体。 如果 `c` 不是 `'a'` 或 `'A'` ，则 __`default`__ 执行语句。

**Visual Studio 2017 及更高版本：** （可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用）该 `[[fallthrough]]` 特性是在 c + + 17 标准中指定的。 可以在语句中使用它 __`switch`__ 。 这是一种针对编译器的提示，或读取代码的任何人都是故意的。 Microsoft c + + 编译器当前不会对 fallthrough 行为发出警告，因此此属性不会对编译器行为产生任何影响。 在此示例中，特性应用于未终止标记的语句中的空语句。 换句话说，分号是必需的。

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 版本15.3 及更高版本**（可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用）。 __`switch`__ 语句可能包含以 *`init-statement`* 分号结尾的子句。 它会引入和初始化一个变量，该变量的范围限于语句的块 __`switch`__ ：

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

语句的内部块 __`switch`__ 可以包含具有初始值设定项的定义，只要它们是可*访问*的，即不会被所有可能的执行路径跳过。 使用这些声明引入的名称具有局部范围。 例如：

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

__`switch`__ 语句可以嵌套。 嵌套时， __`case`__ 或 __`default`__ 标签与包含它们的最近的语句相关联 __`switch`__ 。

### <a name="microsoft-specific-behavior"></a>特定于 Microsoft 的行为

Microsoft c + + 不会限制 __`case`__ 语句中值的数目 __`switch`__ 。 该数量仅受可用内存的限制。

## <a name="see-also"></a>请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
