---
title: return 语句 (C)
description: C 语言 return 语句会结束函数的执行并选择性地将值返回给调用方。
ms.date: 06/10/2020
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: 7d518aa17185c96de15c8f9aa9b65ae5c72bd014
ms.sourcegitcommit: 01b911613606c3fc92cbd9ca48cca6046a7e8258
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716289"
---
# <a name="return-statement-c"></a>return 语句 (C)

`return` 语句会结束函数的执行并返回对调用函数的控制。 紧接在调用之后在调用函数中恢复执行。 `return` 语句可将值返回给调用函数。 有关详细信息，请参阅[返回类型](../c-language/return-type.md)。

## <a name="syntax"></a>语法

> *jump-statement*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`return`** *expression*&#8203;<sub>opt</sub> **`;`**

如果表达式存在的话，*expression* 的值将返回到调用函数。 如果 *expression* 省略，该函数返回值未定义。 先计算表达式（如果存在），然后转换为函数返回的类型。 如果 `return` 语句在具有 `void` 返回类型的函数中包含表达式，则编译器会生成一个警告，并且不计算该表达式 。

如果函数定义中未出现 `return` 语句，则在执行被调用函数的最后一个语句后，控件自动返回到调用函数。 在这种情况下，当调用该函数时，返回值将未定义。 如果函数具有 `void` 以外的返回类型，则这是一个严重的 bug，编译器会打印一条警告诊断消息。 如果函数具有 `void` 返回类型，则此行为正常，但可能被视为不良样式。 请使用纯文本 `return` 语句阐明意图。

一个好的工程实践是始终为函数指定一个返回类型。 如果不需要返回值，请将函数声明为具有 `void` 返回类型。 如果未指定返回类型，则 C 编译器会假定默认返回类型 `int`。

许多程序员使用括号将 `return`语句的表达式参数括起来。 但是，C 不需要括号。

如果该编译器发现 `return` 语句后放置了任何语句，则它可能会发出一条警告诊断消息，指出代码无法访问。

在 `main` 函数中，`return` 语句和表达式是可选的 。 返回的值（若指定了返回值）发生的情况取决于实现。 **Microsoft 专用**：Microsoft C 实现会将表达式值返回给调用程序的进程，例如 `cmd.exe`。 如果未提供 `return` 表达式，则 Microsoft C 运行时会返回一个值来指示成功 (0) 还是失败（非零值）。

## <a name="example"></a>示例

以下示例是一个程序，很多部分都用到了它。 它演示了 `return` 语句，还演示了如何使用它来结束函数执行和根据需要返回值。

```C
// C_return_statement.c
// Compile using: cl /W4 C_return_statement.c
#include <limits.h>      // for INT_MAX
#include <stdio.h>       // for printf

long long square( int value )
{
    // Cast one operand to long long to force the
    // expression to be evaluated as type long long.
    // Note that parentheses around the return expression
    // are allowed, but not required here.
    return ( value * (long long) value );
}
```

`square` 函数在更大范围的类型中返回其参数的平方，以防止出现算术错误。 **Microsoft 专用**：在 Microsoft C 实现中，`long long` 类型足够大，可容纳两个 `int` 值的乘积而不出现溢出 。

`square` 中 `return` 表达式两侧的括号在计算时被看做是表达式的一部分，`return` 语句不需要使用括号 。

```C
double ratio( int numerator, int denominator )
{
    // Cast one operand to double to force floating-point
    // division. Otherwise, integer division is used,
    // then the result is converted to the return type.
    return numerator / (double) denominator;
}
```

`ratio` 函数会以浮点 `double` 值的形式返回其两个 `int` 参数之比 。 `return` 表达式被强制使用浮点运算，方式是将其中一个操作数强制转换为 `double` 。 否则，会使用整除运算符，而小数部分将丢失。

```C
void report_square( void )
{
    int value = INT_MAX;
    long long squared = 0LL;
    squared = square( value );
    printf( "value = %d, squared = %lld\n", value, squared );
    return; // Use an empty expression to return void.
}
```

`report_square` 函数使用 `INT_MAX` 的参数值调用 `square`，INT_MAX 是适合 `int` 的最大带符号整数值。 `long long` 结果存储在 `squared` 中，然后打印出来。 `report_square` 函数具有 `void` 返回类型，因此它的 `return` 语句中没有表达式 。

```C
void report_ratio( int top, int bottom )
{
    double fraction = ratio( top, bottom );
    printf( "%d / %d = %.16f\n", top, bottom, fraction );
    // It's okay to have no return statement for functions
    // that have void return types.
}
```

`report_ratio` 函数使用 `1` 和 `INT_MAX` 的参数值调用 `ratio`。 `double` 结果存储在 `fraction` 中，然后打印出来。 `report_ratio` 函数具有 `void` 返回类型，因此无需显式返回值。 `report_ratio` 的执行被放弃，不会向调用方返回任何值。

```C
int main()
{
    int n = 1;
    int x = INT_MAX;

    report_square();
    report_ratio( n, x );

    return 0;
}
```

`main` 函数会调用两个值：`report_square` 和 `report_ratio`。 由于 `report_square` 不采用任何参数且返回 `void`因此我们不会将其结果分配给变量。 同样地，`report_ratio` 会返回 `void`，因此我们不保存它的返回值。 在上述每个函数调用后，都继续在下一条语句执行。 然后，`main` 会返回值 `0`（通常用于报告成功）来结束程序。

要编译该示例，请创建一个名为 `C_return_statement.c` 的源代码文件。 然后，按照所示顺序复制所有示例代码。 保存文件，再使用以下命令在开发人员命令提示窗口中编译它：

**`cl /W4 C_return_statement.c`**

然后，在命令提示符处输入 `C_return_statement.exe` 来运行示例代码。 该示例的输出与以下内容类似：

```Output
value = 2147483647, squared = 4611686014132420609
1 / 2147483647 = 0.0000000004656613
```

## <a name="see-also"></a>请参阅

[语句](../c-language/statements-c.md)
