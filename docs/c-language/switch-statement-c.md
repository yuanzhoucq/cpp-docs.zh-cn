---
title: switch语句（C）
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: 5858447602a28dcc5573aa3138e869d106b5aa23
ms.sourcegitcommit: 2f9ff2041d70c406df76c5053151192aad3937ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587374"
---
# <a name="switch-statement-c"></a>`switch`语句（C）

__`switch`__ 和__`case`__ 语句帮助控制复杂的条件和分支运算。 __`switch`__ 语句将控制权转交给其主体中的语句。

## <a name="syntax"></a>语法

> *`selection-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>备注

__`switch`__ 语句会使控件在其语句体*`labeled-statement`* 中传输到一个语句，具体取决于的*`expression`* 值。

*`expression`* 和每个*`constant-expression`* 的值必须具有整型类型。 在*`constant-expression`* 编译时，必须有明确的常量整数值。

Control 传递到其**`case`** *`constant-expression`* 值与的值匹配的语句*`expression`*。 __`switch`__ 语句可以包含任意数量的__`case`__ 实例。 但是，同一__`switch`__ 语句*`constant-expression`* 中的两个值不能具有相同的值。 __`switch`__ 语句体的执行从匹配*`labeled-statement`* 中或之后的第一个语句开始。 执行将一直持续到主体的末尾，或直到__`break`__ 语句将控制权转移到主体。

__`switch`__ 语句的使用通常类似于：

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

您可以使用__`break`__ 语句来结束__`switch`__ 语句中特定标记语句的处理。 它分支到__`switch`__ 语句的末尾。 如果__`break`__ 没有，程序将继续执行下一个标记语句，执行语句，直到__`break`__ 到达语句的或末尾。 在某些情况下，可能需要此继续符。

如果__`default`__ 没有__`case`__ *`constant-expression`* 值等于的*`expression`* 值，则执行语句。 如果没有__`default`__ 语句，并且找不到__`case`__ 匹配项，则不会执行__`switch`__ 正文中的任何语句。 最多只能有一个__`default`__ 语句。 __`default`__ 语句无需到达末尾。 它可以出现在__`switch`__ 语句主体中的任何位置。 __`case`__ 或__`default`__ 标签只能出现在__`switch`__ 语句中。

__`switch`__ *`expression`* 和__`case`__ 的*`constant-expression`* 类型必须是整型。 每个__`case`__ *`constant-expression`* 的值在语句体中必须是唯一的。

语句体的主体的__`case`__ 和__`default`__ 标签只在用于确定语句体中开始执行的初始测试中才有意义。 __`switch`__ __`switch`__ 语句可以嵌套。 在执行到任何__`switch`__ 语句之前，将初始化所有静态变量。

> [!NOTE]
> 声明可以出现在构成__`switch`__ 主体的复合语句的开头，但不执行包含在声明中的初始化。 __`switch`__ 语句将控制直接传输到正文中的可执行语句，并绕过包含初始化的行。

下面的示例阐释__`switch`__ 了语句：

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

__`switch`__ 如果`c`等于`'A'`，则会执行此示例中主体的所有三个语句，因为在__`break`__ 以下__`case`__ 项之前不会出现语句。 将执行控制转交给第一个语句 (`capital_a++;`) 并继续按顺序转交给主体的其余部分。 如果 `c` 等于 `'a'`，则 `letter_a` 和 `total` 将增加。 仅`total`当不等于`c` `'A'`或`'a'`时，才会递增。

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

在此示例中， __`break`__ 语句位于__`switch`__ 主体的每个语句之后。 __`break`__ 语句在执行一条语句之后强制从语句体中退出。 如果 `i` 等于 -1，则仅 `n` 将增加。 __`break`__ 下面的语句`n++;`将导致执行控制传递出语句体，并绕过剩余语句。 同样，如果 `i` 等于 0，则仅 `z` 将增加；如果 `i` 等于 1，则仅 `p` 将增加。 最后一个__`break`__ 语句并不是必需的，因为控件在复合语句的结尾处越过了正文。 提供此方法是为了保持一致性。

单个语句可以有多个__`case`__ 标签，如以下示例所示：

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

在此示例中，如果 *constant-expression* 等于 `'a'` 和 `'f'` 之间的任何字母，则调用 `convert_hex` 函数。

### <a name="microsoft-specific"></a>Microsoft 专用

Microsoft C 不会限制__`case`__ __`switch`__ 语句中值的数目。 该数量仅受可用内存的限制。 ANSI C 要求__`switch`__ 语句中至少__`case`__ 允许257个标签。

Microsoft default C 的是启用 microsoft 扩展。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)编译器选项禁用这些扩展。

## <a name="see-also"></a>请参阅

[switch语句（c + +）](../cpp/switch-statement-cpp.md)
