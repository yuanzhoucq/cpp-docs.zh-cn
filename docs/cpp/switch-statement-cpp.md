---
title: :::no-loc(switch):::语句（c + +）
description: 'Microsoft Visual Studio c + + 中对标准 c + + 语句的引用 :::no-loc(switch)::: 。'
ms.date: 04/25/2020
f1_keywords:
- :::no-loc(default):::_cpp
- :::no-loc(switch):::_cpp
- :::no-loc(case):::_cpp
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C++]'
- ':::no-loc(case)::: keyword [C++], in :::no-loc(switch)::: statements'
- ':::no-loc(default)::: keyword [C++]'
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
- ':::no-loc(while):::'
- ':::no-loc(opt):::'
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d71989b6d8af0213c4cd6d4fbd8d5a84b318701a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223585"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`语句（c + +）

允许根据整型表达式的值在多个代码段中进行选择。

## <a name="syntax"></a>语法

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;**`:::no-loc(switch):::`**&nbsp;**`(`**&nbsp;*`init-statement`*<sub>:::no-loc(opt):::</sub><sup>C + + 17</sup>&nbsp;*`condition`*&nbsp;**`)`**&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>:::no-loc(opt):::</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>备注

`:::no-loc(switch):::` 语句使控件根据 `condition` 的值转移到其语句正文中的一个 `labeled-statement`  。

*`condition`* 必须具有整型类型，或者是具有到整型的明确转换的类类型。 整数提升的发生方式如[标准转换](standard-conversions.md)中所述。

**`:::no-loc(switch):::`** 语句体包含一系列 **`:::no-loc(case):::`** 标签和一个 :::no-loc(opt)::: ional **`:::no-loc(default):::`** 标签。 *`labeled-statement`* 是以下标签和后面的语句之一。 带标签的语句无语法要求，但如果 **`:::no-loc(switch):::`** 没有这些语句，语句就毫无意义了。 语句中的两个 *`constant-expression`* 值的 **`:::no-loc(case):::`** 计算结果不能为相同的值。 **`:::no-loc(default):::`** 标签只能出现一次。 **`:::no-loc(default):::`** 语句通常放置在末尾，但它可以出现在语句体中的任何位置 **`:::no-loc(switch):::`** 。 `:::no-loc(case):::` 或 `:::no-loc(default):::` 标签只能显示在 `:::no-loc(switch):::` 语句内部    。

*`constant-expression`* 每个标签中的 **`:::no-loc(case):::`** 会转换为与相同类型的常数值 *`condition`* 。 然后，比较与是否 *`condition`* 相等。 控件将传递到值后的第一条语句 **`:::no-loc(case):::`** *`constant-expression`* *`condition`* 。 下表中显示了生成的行为。

### <a name="no-locswitch-statement-behavior"></a>`:::no-loc(switch):::`语句行为

| 条件 | 操作 |
|--|--|
| 转换后的值与提升的控制表达式的值匹配。 | 控制将转移到跟在该标签后面的语句。 |
| 没有常量与标签中的常量匹配 **`:::no-loc(case):::`** ; 有一个 **`:::no-loc(default):::`** 标签。 | 控制将转移到 **`:::no-loc(default):::`** 标签。 |
| 没有常量与标签中的常量匹配 **`:::no-loc(case):::`** ; 不存在任何 **`:::no-loc(default):::`** 标签。 | 控制在语句后传递到语句 **`:::no-loc(switch):::`** 。 |

如果找到匹配的表达式，则执行可以继续，稍后 **`:::no-loc(case):::`** 或 **`:::no-loc(default):::`** 标签。 [`:::no-loc(break):::`](../cpp/:::no-loc(break):::-statement-cpp.md)语句用于停止执行并将控制转移到语句后面的语句 **`:::no-loc(switch):::`** 。 如果没有 **`:::no-loc(break):::`** 语句，则将执行从匹配的标签到末尾的每个语句 **`:::no-loc(case):::`** **`:::no-loc(switch):::`** ，包括 **`:::no-loc(default):::`** 。 例如：

```cpp
// :::no-loc(switch):::_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, other;
   char c;
   upper:::no-loc(case):::_A = lower:::no-loc(case):::_a = other = 0;

   :::no-loc(while)::: ( c = *buffer++ )   // Walks buffer until NULL
   {
      :::no-loc(switch)::: ( c )
      {
         :::no-loc(case)::: 'A':
            upper:::no-loc(case):::_A++;
            :::no-loc(break):::;
         :::no-loc(case)::: 'a':
            lower:::no-loc(case):::_a++;
            :::no-loc(break):::;
         :::no-loc(default)::::
            other++;
      }
   }
   printf_s( "\nUpper:::no-loc(case)::: A: %d\nLower:::no-loc(case)::: a: %d\nTotal: %d\n",
      upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, (upper:::no-loc(case):::_A + lower:::no-loc(case):::_a + other) );
}
```

在上面的示例中， `upper:::no-loc(case):::_A` 如果是大写，则将递增 `c` :::no-loc(case)::: `'A'` 。 **`:::no-loc(break):::`** 后的语句 `upper:::no-loc(case):::_A++` 终止了 **`:::no-loc(switch):::`** 语句体的执行，并将控制权传递到 **`:::no-loc(while):::`** 循环。 如果没有 **`:::no-loc(break):::`** 语句，执行将 "贯穿" 到下一个标记语句，因此 `lower:::no-loc(case):::_a` 和也将 `other` 递增。 的语句将提供类似的目的 **`:::no-loc(break):::`** `:::no-loc(case)::: 'a'` 。 如果 `c` 是较小的 :::no-loc(case)::: `'a'` ， `lower:::no-loc(case):::_a` 则递增， **`:::no-loc(break):::`** 语句将终止 **`:::no-loc(switch):::`** 语句体。 如果 `c` 不是 `'a'` 或 `'A'` ，则 **`:::no-loc(default):::`** 执行语句。

**Visual Studio 2017 及更高版本：** （可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用）该 `[[fallthrough]]` 特性是在 c + + 17 标准中指定的。 可以在语句中使用它 **`:::no-loc(switch):::`** 。 这是一种针对编译器的提示，或读取代码的任何人都是故意的。 Microsoft c + + 编译器当前不会对 fallthrough 行为发出警告，因此此属性不会对编译器行为产生任何影响。 在此示例中，特性应用于未终止标记的语句中的空语句。 换句话说，分号是必需的。

```cpp
int main()
{
    int n = 5;
    :::no-loc(switch)::: (n)
    {

    :::no-loc(case)::: 1:
        a();
        :::no-loc(break):::;
    :::no-loc(case)::: 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    :::no-loc(case)::: 3:
        c();
        :::no-loc(break):::;
    :::no-loc(default)::::
        d();
        :::no-loc(break):::;
    }

    return 0;
}
```

**Visual Studio 2017 版本15.3 及更高版本**（可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用）。 **`:::no-loc(switch):::`** 语句可能包含以 *`init-statement`* 分号结尾的子句。 它会引入和初始化一个变量，该变量的范围限于语句的块 **`:::no-loc(switch):::`** ：

```cpp
    :::no-loc(switch)::: (Gadget gadget(args); auto s = gadget.get_status())
    {
    :::no-loc(case)::: status::good:
        gadget.zip();
        :::no-loc(break):::;
    :::no-loc(case)::: status::bad:
        throw BadGadget();
    };
```

语句的内部块 **`:::no-loc(switch):::`** 可以包含具有初始值设定项的定义，只要它们是可*访问*的，即不会被所有可能的执行路径跳过。 使用这些声明引入的名称具有局部范围。 例如：

```cpp
// :::no-loc(switch):::_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    :::no-loc(switch):::( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    :::no-loc(case)::: 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        :::no-loc(break):::;

    :::no-loc(case)::: 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        :::no-loc(break):::;

    :::no-loc(default)::::
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        :::no-loc(break):::;
    }
}
```

**`:::no-loc(switch):::`** 语句可以嵌套。 嵌套时， **`:::no-loc(case):::`** 或 **`:::no-loc(default):::`** 标签与包含它们的最近的语句相关联 **`:::no-loc(switch):::`** 。

### <a name="microsoft-specific-behavior"></a>特定于 Microsoft 的行为

Microsoft c + + 不会限制 **`:::no-loc(case):::`** 语句中值的数目 **`:::no-loc(switch):::`** 。 该数量仅受可用内存的限制。

## <a name="see-also"></a>另请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
