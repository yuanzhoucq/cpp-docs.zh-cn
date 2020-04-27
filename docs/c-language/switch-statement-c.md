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
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167671"
---
# <a name="opno-locswitch-statement-c"></a>switch语句（C）

**switch** 和**case** 语句帮助控制复杂的条件和分支运算。 **switch** 语句将控制权转交给其主体中的语句。

## <a name="syntax"></a>语法

*selection-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***expression* **`)`** *语句*

*标记语句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *常量表达式*  **`:`**  *语句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *损益*

Control 传递到其**case** *常量表达式*与** switch （** *expression* **）** 的值匹配的语句。 **switch** 语句可以包含任意数量的**case** 实例。 但是，同一**switch** 语句case中的两个常量不能具有相同的值。 语句体的执行从选定语句处开始。 它会一直持续到主体的末尾，或直到**break** 语句将控制权转移到主体。

**switch** 语句的使用通常类似于：

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

您可以使用**break** 语句来结束**switch** 语句中特定标记语句的处理。 它分支到**switch** 语句的末尾。 如果**break** 没有，程序将继续执行下一个标记语句，执行语句，直到**break** 到达语句的或末尾。 在某些情况下，可能需要此继续符。

如果**default** 没有**case** *常数表达式*等于** switch （** *expression* **）** 的值，则执行语句。 如果没有**default** 语句，并且找不到**case** 匹配项，则不会执行**switch** 正文中的任何语句。 最多只能有一个**default** 语句。 **default** 语句无需到达末尾。 它可以出现在**switch** 语句主体中的任何位置。 **case** 或**default** 标签只能出现在**switch** 语句中。

**switch** *表达式*和**case** *常量表达式*的类型必须是整型。 每个**case** *常量表达式*的值在语句体中必须是唯一的。

语句体的主体的**case** 和**default** 标签只在用于确定语句体中开始执行的初始测试中才有意义。 **switch** **switch** 语句可以嵌套。 在执行到任何**switch** 语句之前，将初始化所有静态变量。

> [!NOTE]
> 声明可以出现在构成**switch** 主体的复合语句的开头，但不执行包含在声明中的初始化。 **switch** 语句将控制直接传输到正文中的可执行语句，并绕过包含初始化的行。

下面的示例阐释**switch** 了语句：

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

**switch** 如果`c`等于`'A'`，则会执行此示例中主体的所有三个语句，因为在**break** 以下case项之前不会出现语句。 将执行控制转交给第一个语句 (`capital_a++;`) 并继续按顺序转交给主体的其余部分。 如果 `c` 等于 `'a'`，则 `letter_a` 和 `total` 将增加。 仅`total`当不等于`c` `'A'`或`'a'`时，才会递增。

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

在此示例中， **break** 语句位于**switch** 主体的每个语句之后。 **break** 语句在执行一条语句之后强制从语句体中退出。 如果 `i` 等于 -1，则仅 `n` 将增加。 **break** 下面的语句`n++;`将导致执行控制传递出语句体，并绕过剩余语句。 同样，如果 `i` 等于 0，则仅 `z` 将增加；如果 `i` 等于 1，则仅 `p` 将增加。 最后一个**break** 语句并不是必需的，因为控件在复合语句的结尾处越过了正文。 提供此方法是为了保持一致性。

单个语句可以有多个**case** 标签，如以下示例所示：

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

Microsoft C 不会限制case **switch** 语句中值的数目。 该数量仅受可用内存的限制。 ANSI C 要求**switch** 语句中至少case允许257个标签。

Microsoft default C 的是启用 microsoft 扩展。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)编译器选项禁用这些扩展。

## <a name="see-also"></a>另请参阅

[switch语句（c + +）](../cpp/switch-statement-cpp.md)
