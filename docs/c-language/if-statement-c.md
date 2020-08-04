---
title: if 语句 (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: 67cdae033c3c8669c8bc7ae1d2e3584ef68498f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227837"
---
# <a name="if-statement-c"></a>if 语句 (C)

`if` 语句控制条件分支。 如果表达式的值不为零，则执行 `if` 语句的主体。 `if` 语句的语法有两种形式。

## <a name="syntax"></a>语法

*selection-statement*: **if (**  *expression*  **)**  *statement*

if (  expression  )  statement  `else`  statement

在 `if` 语句的两种形式中，计算除了结构之外可以有任何值的表达式，包括所有副作用。

在第一种形式的语法中，如果 expression  为 true（非零），则执行 statement  。 如果 expression  为 false，则忽略 statement  。 在使用 `else` 的第二种语法形式中，如果 expression 为 false，则执行第二个 statement。 对于这两种形式，控制权随后从 `if` 语句传递给程序中的下一个语句，除非其中一个语句包含 `break`、`continue` 或 `goto`。

下面的几个示例展示了 `if` 语句：

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

在此示例中，如果 `y = x/i;` 大于 0，则执行 `i` 语句。 如果 `i` 小于或等于 0，则将 `i` 赋给 `x`，并将 `f( x )` 赋给 `y`。 请注意，构成 `if` 子句的语句以分号结尾。

嵌套 `if` 语句和 `else` 子句时，请使用大括号将语句和子句组合成复合语句，以阐明你的意图。 如果没有大括号，编译器会将每个 `else` 与缺少 `else` 的最近 `if` 关联，从而解决二义性。

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

在此示例中，`else` 子句与内部 `if` 语句关联。 如果 `i` 小于或等于 0，则不会将任何值赋给 `x`。

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

此示例中的内部 `if` 语句两边的大括号让 `else` 子句成为外部 `if` 语句的一部分。 如果 `i` 小于或等于 0，则将 `i` 赋给 `x`。

## <a name="see-also"></a>请参阅

[if-else 语句 (C++)](../cpp/if-else-statement-cpp.md)
