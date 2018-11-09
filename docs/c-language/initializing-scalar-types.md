---
title: 初始化标量类型
ms.date: 11/04/2016
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
ms.openlocfilehash: f991eff82e5b6919f7960513ae9bc502cad77069
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641085"
---
# <a name="initializing-scalar-types"></a>初始化标量类型

初始化标量类型时，assignment-expression 的值将赋给变量。 赋值的转换规则适用。 （有关转换规则的信息，请参阅[类型转换](../c-language/type-conversions-c.md)。）

## <a name="syntax"></a>语法

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer* /\* For scalar initialization \*/

*initializer*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*

您可初始化任何类型的变量，前提是遵循下列规则：

- 在文件范围级别声明的变量可初始化。 如果未显式初始化外部级别的变量，则默认情况下它将初始化为 0。

- 常量表达式可用于初始化使用 static storage-class-specifier 声明的任何全局变量。 程序开始执行时将初始化声明为 static 的变量。 如果未显式初始化全局 static 变量，则默认情况下该变量将初始化为 0，并且具有指针类型的所有成员都将赋给 null 指针。

- 使用 auto 或 register 存储类说明符声明的变量将在执行控制每次传递到声明它的块中时进行初始化。 如果省略 auto 或 register 变量的声明中的初始值设定项，则变量的初始值是不确定的。 对于自动值和寄存器值，初始值设定项未限制为常量；它可以是包含之前定义的值的任何表达式，甚至是函数调用。

- 外部变量声明和所有 static 变量（无论外部还是内部）的初始值必须是常量表达式。 （有关详细信息，请参阅[常量表达式](../c-language/c-constant-expressions.md)。）由于任何外部声明的变量或静态变量的地址为常量，因此可将该地址用于初始化内部声明的 static 指针变量。 但是，auto 变量的地址不能用作静态初始值设定项，因为它可能在每次执行块时都不同。 可使用常量或变量值来初始化 auto 和 register 变量。

- 如果标识符的声明具有块范围，并且标识符具有外部链接，则该声明不能具有初始化。

## <a name="examples"></a>示例

下列示例阐释了初始化：

```C
int x = 10;
```

整数变量 `x` 将初始化为常量表达式 `10`。

```C
register int *px = 0;
```

指针 `px` 将初始化为 0，从而生成“null”指针。

```C
const int c = (3 * 1024);
```

此示例使用常量表达式 `(3 * 1024)` 将 `c` 初始化为因 const 关键字而无法修改的常量值。

```C
int *b = &x;
```

此语句使用另一变量 `b` 的地址初始化指针 `x`。

```C
int *const a = &z;
```

指针 `a` 是使用名为 `z` 的变量的地址初始化的。 但是，由于该指针被指定为 const ，因此变量 `a` 只能被初始化，而始终不能被修改。 该指针始终指向同一位置。

```C
int GLOBAL ;

int function( void )
{
    int LOCAL ;
    static int *lp = &LOCAL;   /* Illegal initialization */
    static int *gp = &GLOBAL;  /* Legal initialization   */
    register int *rp = &LOCAL; /* Legal initialization   */
}
```

全局变量 `GLOBAL` 是在外部级别声明的，因此它具有全局生存期。 局部变量 `LOCAL` 具有 auto 存储类，并且在执行声明它的函数时只具有一个地址。 因此，不允许尝试使用 `LOCAL` 的地址初始化 static 指针变量 `lp`。 static 指针变量 `gp` 可初始化为 `GLOBAL` 的地址，因为该地址始终相同。 同样，`*rp` 可初始化，因为 `rp` 是局部变量，并且可具有非常量初始值设定项。 每次输入块时，`LOCAL` 都具有新地址，该地址之后将赋给 `rp`。

## <a name="see-also"></a>请参阅

[初始化](../c-language/initialization.md)