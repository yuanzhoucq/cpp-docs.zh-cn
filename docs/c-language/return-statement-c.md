---
title: return 语句 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: c3975076ee65d267f3d278e20a7770e6750c06d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148980"
---
# <a name="return-statement-c"></a>return 语句 (C)

`return` 语句终止函数的执行并返回对调用函数的控制。 紧接在调用之后在调用函数中恢复执行。 `return` 语句还可以将值返回给调用函数。 有关详细信息，请参阅[返回类型](../c-language/return-type.md)。

## <a name="syntax"></a>语法

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *expression*<sub>opt</sub> **;**

如果表达式存在的话，*expression* 的值将返回到调用函数。 如果 *expression* 省略，该函数返回值未定义。 先计算表达式（如果存在），然后转换为函数返回的类型。 如果使用返回类型 `void` 声明函数，包含表达式的 `return` 语句生成警告，并且该表达式不进行计算。

如果在函数定义中 `return` 语句未出现，在执行被调用函数的最后一个语句后，控件自动返回到调用函数。 在这种情况下，当调用该函数时，返回值将未定义。 如果不需要返回值，声明该函数具有 `void` 返回类型；否则，默认返回类型为 `int`。

许多程序员使用括号括住 `return` 语句的*表达式*参数。 但是，C 不需要括号。

此示例演示了 `return` 语句：

```C
#include <limits.h>
#include <stdio.h>

void draw( int i, long long ll );
long long sq( int s );

int main()
{
    long long y;
    int x = INT_MAX;

    y = sq( x );
    draw( x, y );
    return x;
}

long long sq( int s )
{
    // Note that parentheses around the return expression
    // are allowed but not required here.
    return( s * (long long)s );
}

void draw( int i, long long ll )
{
    printf( "i = %d, ll = %lld\n", i, ll );
    return;
}
```

在此示例中，`main` 函数调用两个函数 `sq` 和 `draw`。 `sq` 函数返回 `x * x` 的值为 `main`，其中返回值分配给 `y`。 `sq` 中的返回表达式两边的括号作为表达式的一部分进行计算，返回语句不需要括号。 由于先计算返回表达式，然后将其转换为返回类型，因此 `sq` 强制表达式类型为使用强制转换的返回类型，以防止可能导致意外结果的整数溢出。 `draw` 函数声明为 `void` 函数。 它打印参数的值，然后空返回语句结束该函数且不返回值。 尝试赋值 `draw` 的返回值会导致发布诊断信息。 随后，`main` 函数将 `x` 的值返回给操作系统。

该示例的输出与以下内容类似：

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>请参阅

[语句](../c-language/statements-c.md)
