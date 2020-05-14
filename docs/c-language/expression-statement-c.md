---
title: 表达式语句 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233704"
---
# <a name="expression-statement-c"></a>表达式语句 (C)

在执行表达式语句时，将根据[表达式和赋值](../c-language/expressions-and-assignments.md)中概述的规则来计算表达式。

## <a name="syntax"></a>语法

expression-statement  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

在执行下一个语句前，完成表达式计算的所有副作用。 空表达式语句被称为 null 语句。 有关详细信息，请参阅 [Null 语句](../c-language/null-statement-c.md)。

这些示例演示了表达式语句。

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

在最后一个语句中，函数调用表达式的值（包括函数返回的任何值）增加 3，然后被赋给变量 `y` 和 `z`。

## <a name="see-also"></a>请参阅

[语句](../c-language/statements-c.md)
