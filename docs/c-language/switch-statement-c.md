---
title: ':::no-loc(switch)::: 语句 (C)'
ms.date: 04/25/2020
f1_keywords:
- ':::no-loc(switch):::'
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C]'
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
ms.openlocfilehash: bdd6885f67728a3c81e395f05c33191156896ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220777"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::` 语句 (C)

**`:::no-loc(switch):::`** 和 **`:::no-loc(case):::`** 语句帮助控制复杂条件和分支运算。 **`:::no-loc(switch):::`** 语句将控制权转交给其正文中的语句。

## <a name="syntax"></a>语法

> *`selection-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(switch)::: (`** &nbsp; *`expression`* &nbsp; **`)`** &nbsp; *`statement`*

> *`labeled-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`** &nbsp; *`constant-expression`* &nbsp; **`:`** &nbsp; *`statement`* \
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`** &nbsp; **`:`** &nbsp; *`statement`*

## <a name="remarks"></a>备注

`:::no-loc(switch):::` 语句使控件根据 `expression` 的值转移到其语句正文中的一个 `labeled-statement`  。

`expression` 和每个 `constant-expression` 的值必须有一个整型类型   。 在编译时，`constant-expression` 必须有一个明确的常数整型值  。

控件传递给 `:::no-loc(case):::` 语句，该语句的 `constant-expression` 值与 `expression` 值匹配    。 `:::no-loc(switch):::` 语句可以包含任意数量的 `:::no-loc(case):::` 实例。 但是，同一个 `:::no-loc(switch):::` 语句中的两个 `constant-expression` 值不能具有相同的值  。 `:::no-loc(switch):::` 语句正文的执行从匹配的 `labeled-statement` 中或之后的第一个语句开始  。 执行一直持续到正文的末尾，或者直到 `:::no-loc(break):::` 语句将控制权从主体中传出。

`:::no-loc(switch):::` 语句的使用通常类似于：

```C
:::no-loc(switch)::: ( expression )
{
    // declarations
    // . . .
    :::no-loc(case)::: constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        :::no-loc(break):::;
    :::no-loc(default)::::
        // statements executed if expression does not equal
        // any :::no-loc(case)::: constant_expression
}
```

可以使用 `:::no-loc(break):::` 语句结束 `:::no-loc(switch):::` 语句中特定标记语句的处理。 它分支到 `:::no-loc(switch):::` 语句的结尾。 如果不使用 `:::no-loc(break):::` ，则程序会继续到下一标记语句，并执行语句，直到达到 `:::no-loc(break):::` 或该语句的末尾。 在某些情况下，可能需要此继续符。

如果没有 `:::no-loc(case):::` `constant-expression` 值等于 `expression`，则执行 `:::no-loc(default):::` 语句   。 如果没有 `:::no-loc(default):::` 语句，并且找不到`:::no-loc(case):::`  匹配，则 `:::no-loc(switch):::` 正文中的任何语句都不会执行。 最多可以有一个 `:::no-loc(default):::` 语句。 `:::no-loc(default):::` 语句不必在末尾出现。 它可能出现在 `:::no-loc(switch):::` 语句正文中的任何位置。 `:::no-loc(case):::` 或 `:::no-loc(default):::` 标签只能显示在 `:::no-loc(switch):::` 语句内部    。

`:::no-loc(switch):::` `expression` 和 `:::no-loc(case):::` `constant-expression` 的类型必须为整型     。 每个 `:::no-loc(case):::``constant-expression` 的值在语句正文中必须是唯一的   。

`:::no-loc(switch):::` 语句正文的 `:::no-loc(case):::` 和 `:::no-loc(default):::` 标签只在初始测试中有意义，该测试将确定语句体中开始执行的位置    。 可以嵌套 `:::no-loc(switch):::` 语句。 在执行到任何 `:::no-loc(switch):::` 语句中之前，初始化任何静态变量。

> [!NOTE]
> 声明可以出现在构成 `:::no-loc(switch):::` 正文的复合语句的前面，但不执行包含在声明中的初始化。 `:::no-loc(switch):::` 语句将控制权直接转交给正文中的一个可执行语句，并绕过包含初始化的行。

以下示例演示了 `:::no-loc(switch):::` 语句：

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'A':
        capital_a++;
    :::no-loc(case)::: 'a':
        letter_a++;
    :::no-loc(default)::: :
        total++;
}
```

如果 `c` 等于 `'A'`，则会执行此示例中的 `:::no-loc(switch):::` 正文的所有三个语句，因为不会在以下 `:::no-loc(case):::` 前显示 `:::no-loc(break):::` 语句。 将执行控制转交给第一个语句 (`capital_a++;`) 并继续按顺序转交给主体的其余部分。 如果 `c` 等于 `'a'`，则 `letter_a` 和 `total` 将增加。 当 `c` 不等于 `'A'` 或 `'a'` 时，仅递增 `total`。

```C
:::no-loc(switch):::( i )
{
    :::no-loc(case)::: -1:
        n++;
        :::no-loc(break):::;
    :::no-loc(case)::: 0 :
        z++;
        :::no-loc(break):::;
    :::no-loc(case)::: 1 :
        p++;
        :::no-loc(break):::;
}
```

在此示例中，`:::no-loc(break):::` 语句跟在 `:::no-loc(switch):::` 正文的每个语句的后面   。 在执行一个语句后，`:::no-loc(break):::` 语句将强制从语句正文中退出  。 如果 `i` 等于 -1，则仅 `n` 将增加。 `n++;` 语句后面的 `:::no-loc(break):::` 会导致执行控制传递出语句正文，并绕过剩余语句  。 同样，如果 `i` 等于 0，则仅 `z` 将增加；如果 `i` 等于 1，则仅 `p` 将增加。 从严格意义上讲，最后的 `:::no-loc(break):::` 语句不是必需的，因为控制权将在复合语句的结尾传递出语句正文  。 包含此语句是为了获得一致性。

如下面的示例所示，一个语句可以包含多个 `:::no-loc(case):::` 标签  ：

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'a' :
    :::no-loc(case)::: 'b' :
    :::no-loc(case)::: 'c' :
    :::no-loc(case)::: 'd' :
    :::no-loc(case)::: 'e' :
    :::no-loc(case)::: 'f' :  convert_hex(c);
}
```

在此示例中，如果 *constant-expression* 等于 `'a'` 和 `'f'` 之间的任何字母，则调用 `convert_hex` 函数。

### <a name="microsoft-specific"></a>Microsoft 专用

Microsoft C 未限制 `:::no-loc(switch):::` 语句中 `:::no-loc(case):::` 值的数量   。 该数量仅受可用内存的限制。 ANSI C 要求 `:::no-loc(switch):::` 语句内至少允许使用 257 个 `:::no-loc(case):::` 标签   。

Microsoft C 的 :::no-loc(default)::: 是启用 Microsoft 扩展。 使用 [/Za](../build/reference/za-ze-disable-language-extensions.md) 编译器选项禁用这些扩展。

## <a name="see-also"></a>请参阅

[:::no-loc(switch):::语句 (C++)](../cpp/:::no-loc(switch):::-statement-cpp.md)
