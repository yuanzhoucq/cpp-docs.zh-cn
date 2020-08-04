---
title: C 常量表达式
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: 38d4eff6cf764a30bf409032ac692189d1300315
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213731"
---
# <a name="c-constant-expressions"></a>C 常量表达式

常量表达式将在编译时而不是运行时计算，并且可在可使用常量的任何位置使用。 常量表达式的计算结果必须是位于该类型的可表示值范围内的常量。 常数表达式的操作数可以是整型常数、字符常数、浮点常数、枚举常数、类型强制转换、`sizeof` 表达式和其他常数表达式。

## <a name="syntax"></a>语法

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;conditional-expression

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression* **?** *expression* **:** *conditional-expression*

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignment-expression*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;conditional-expression<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*assignment-operator*: one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

结构声明符、枚举数、直接声明符、直接抽象声明符和标记语句的非终止符包含 *constant-expression* 非终止符。

整型常数表达式必须用于指定结构的位域成员的大小、枚举常数的值、数组的大小或 `case` 常数的值。

预处理器指令中使用的常量表达式受其他限制的约束。 因此，它们被称为“受限制的常量表达式”。 受限制的常数表达式不能包含 `sizeof` 表达式、枚举常数、转换为任何类型的类型强制转换或浮点类型常数。 但它可包含定义的特殊常量表达式 defined (_identifier_)   。

## <a name="see-also"></a>请参阅

- [操作数和表达式](../c-language/operands-and-expressions.md)
