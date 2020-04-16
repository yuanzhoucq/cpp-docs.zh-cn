---
title: switch语句 （C++）
description: 在 Microsoft 视觉switch工作室C++中引用标准C++语句。
ms.date: 04/15/2020
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
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480826"
---
# <a name="opno-locswitch-statement-c"></a>switch语句 （C++）

允许根据整型表达式的值在多个代码段中进行选择。

## <a name="syntax"></a>语法

> **`switch (`**\[*初始化***`;`**=*表达式***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***常量表达式***`:`***语句*\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***语句*|\
> **`}`**

## <a name="remarks"></a>备注

*表达式*必须具有积分类型，或者是具有明确转换为积分类型的类类型。 积分提升如[标准转换](standard-conversions.md)中所述。

语句**switch** 正文由一系列**case** 标签和可选**default** 标签组成。 总之，标签后的声明称为*标记*语句。 标记的语句不是语法要求，但没有这些语句则**switch** 毫无意义。 语句中的**case** 两个常量表达式不能计算为同一值。 标签**default** 只能显示一次。 语句**default** 通常放在末尾，但它可以出现在**switch** 语句正文的任意位置。 **case** 或**default** 标签只能出现在**switch** 语句中。

每个**case** 标签中的*常量表达式*将转换为*表达式*的类型。 然后，它与相等*表达式*进行比较。 控件传递给常**case***量表达式*与*表达式*的值匹配的语句。 下表中显示了生成的行为。

### <a name="switch-statement-behavior"></a>切换语句行为

| 条件 | 操作 |
|--|--|
| 转换后的值与提升的控制表达式的值匹配。 | 控制将转移到跟在该标签后面的语句。 |
| 没有任何常量与标签中的**case** 常量匹配;存在**default** 标签。 | 控件将转移到标签。 **default** |
| 没有任何常量与标签中的**case** 常量匹配;不存在**default** 标签。 | 控件在**switch** 语句后传输到语句。 |

如果找到匹配的表达式，则执行可以继续执行到以后**case** 或**default** 标签。 语句[`break`](../cpp/break-statement-cpp.md)用于停止执行并在**switch** 语句之后将控制权转移到语句。 如果没有语句**break**，则执行从匹配**case** 标签到**switch** 的末尾的每个语句，包括 。 **default** 例如：

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

在上面的示例中，如果 `uppercase_A` 是大写 `c`，则 `'A'` 将递增。 语句**break** 终止后`uppercase_A++`**switch** 语句正文和控件的执行将传递到循环**while**。 如果没有语句**break**，执行将"通过"到下一个标记的语句，以便`lowercase_a`并且`other`也将递增。 声明也提供了**break** 类似的目的`case 'a'`。 如果`c`是小写`'a'`，`lowercase_a`则递增，**break** 语句终止**switch** 语句正文。 如果`c`不是`'a'`或`'A'`，则执行**default** 语句。

**Visual Studio 2017 及更高版本：（** 可用于[/std：c_17）](../build/reference/std-specify-language-standard-version.md)属性`[[fallthrough]]`在 C++17 标准中指定。 您可以在语句中**switch** 使用它。 这是向编译器或读取代码的任何人的提示，即通过行为是有意的。 Microsoft C++编译器当前不警告失败行为，因此此属性对编译器行为没有影响。 在此示例中，该属性将应用于未终止标记语句中的空语句。 换句话说，分号是必要的。

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

**Visual Studio 2017 版本 15.3 及更高版本**（随[/std：c++17 提供](../build/reference/std-specify-language-standard-version.md)）。 语句switch可能具有*初始化*子句。 它引入并初始化了一个变量，其范围仅限于switch语句块：

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

**switch** 语句的内部块可以包含具有初始化的定义，只要它们*可到达*，也就是说，不会绕过所有可能的执行路径。 使用这些声明引入的名称具有局部范围。 例如：

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

可以**switch** 嵌套语句。 嵌套时，**case** 或**default** 标签与包含它们的最接近**switch** 的语句相关联。

### <a name="microsoft-specific-behavior"></a>特定于微软的行为

Microsoft C 不限制**case****switch** 语句中的值数。 该数量仅受可用内存的限制。 ANSI C 要求在语句中至少**case** 允许 257**switch** 个标签。

default对于 Microsoft C，微软扩展已启用。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)编译器选项禁用这些扩展。

## <a name="see-also"></a>请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
