---
title: '#define 指令 （C/c + +） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#define'
dev_langs:
- C++
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e24c7e020f0008a78d4595577c656003bad359c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765676"
---
# <a name="define-directive-cc"></a>#define 指令 (C/C++)

**#Define**创建*宏*，这是标识符或参数化的标识符与标记字符串的关联。 在定义宏之后，编译器可用标记字符串替换源文件中标识符的每个匹配项。

## <a name="syntax"></a>语法

`#define` *标识符**令牌字符串*<sub>选择</sub>

`#define` *标识符* `(` *标识符*<sub>选择</sub>`,` *...* `,` *标识符*<sub>选择</sub>`)` *令牌字符串*<sub>选择</sub>

## <a name="remarks"></a>备注

**#Define**指令促使编译器来代替*令牌字符串*每个匹配项*标识符*源文件中。 *标识符*构成标记时只会替换。 即*标识符*如果它出现在注释在字符串中，或作为较长的标识符的一部分，则不会替换。 有关详细信息，请参阅[令牌](../cpp/tokens-cpp.md)。

*令牌字符串*参数包含的一系列令牌，如关键字、 常量或完整语句。 一个或多个空白字符必须分隔*令牌字符串*从*标识符*。 此空白不会被视为替换文本的一部分，也不是跟在文本最后一个标记后面的任何空白。

一个`#define`而无需*令牌字符串*移除的匹配项*标识符*源文件中。 *标识符*保持定义，并可以使用测试`#if defined`和`#ifdef`指令。

第二种语法形式定义一个带有参数的类似函数的宏。 此形式接受必须出现在括号内的参数的可选列表。 该宏的定义，每个后续匹配项后*标识符*(*标识符*<sub>选择</sub>，...，*标识符*<sub>opt</sub> ) 使用的版本替换*令牌字符串*替换形参的实参的参数。

形参名称将显示在*令牌字符串*标记实际值的替换的位置。 每个参数名称中可以多次出现*令牌字符串*，并且名称可以按任意顺序出现。 调用中的参数数目必须与宏定义中的自变量数目一致。 对括号的自由使用将确保正确解释复杂的实参。

将用逗号分隔列表中的形参。 列表中的每个名称必须是唯一的，并且列表必须用括号括起。 不能含有空格可分隔*标识符*和左括号。 使用行串连 — 放置一个反斜杠 (`\`) 在换行符前立即-多个源行上的长指令。 正式参数名称的范围扩展到结束的新行*令牌字符串*。

使用第二种语法形式定义宏之后，后面跟有自变量列表的后续文本实例指示一个宏调用。 后面的一个实例的实参*标识符*源文件中与匹配在宏定义中对应的形参。 在每个形参*令牌字符串*的前面没有 stringizing (`#`)、 charizing (`#@`)，或 token-pasting (`##`) 运算符，或后面未跟`##`运算符，替换为对应的实参。 实际自变量中的所有宏都将在指令替换形式参数之前展开。 (在中描述的运算符[预处理器运算符](../preprocessor/preprocessor-operators.md)。)

宏，并自变量的以下示例演示了第二种形式的 **#define**语法：

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

有副作用的自变量有时会导致宏产生意外的结果。 给定的形参可能会超过中出现一次*令牌字符串*。 如果将该形参替换为有副作用的表达式，则可能多次计算该表达式及其副作用。 (请参阅下面的示例[标记粘贴运算符 （#）](../preprocessor/token-pasting-operator-hash-hash.md)。)

`#undef` 指令促使忘记标识符的预处理器定义。 请参阅[#undef 指令](../preprocessor/hash-undef-directive-c-cpp.md)有关详细信息。

如果要定义的宏的名称中会发生*令牌字符串*（甚至由于另一个宏扩展），它展开。

第二个 **#define**为具有相同名称的宏生成一个警告，除非第二个令牌序列等同于第一个。

**Microsoft 专用**

如果新定义在语法上与原始定义相同，则 Microsoft C/C++ 允许您重新定义宏。 换言之，这两个定义可以具有不同的参数名称。 此行为不同于 ANSI C 中，这需要两个定义会从词法上完全相同。

例如，下面两个宏除参数名称外完全相同。 ANSI C 不允许此类重新定义，但 Microsoft C/c + + 编译它时没有错误。

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

另一方面，下面两个宏完全不同，将在 Microsoft C/C++ 中生成一条警告。

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**结束 Microsoft 专用**

此示例演示了 **#define**指令：

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

第一个语句将标识符 `WIDTH` 定义为整数常量 80，并根据 `LENGTH` 将 `WIDTH` 定义为整数常量 10。 `LENGTH` 的每个匹配项将由 (`WIDTH + 10`) 替换。 接下来，`WIDTH + 10` 的每个匹配项将由表达式 (`80 + 10`) 替换。 `WIDTH + 10` 两边的括号非常重要，因为它们控制语句中的解释，如下所示：

```C
var = LENGTH * 20;
```

在预处理阶段之后，语句将变为：

```C
var = ( 80 + 10 ) * 20;
```

其计算结果为 1800。 如果没有括号，则结果将为：

```C
var = 80 + 10 * 20;
```

其计算结果为 280。

**Microsoft 专用**

定义宏和常量[/D](../build/reference/d-preprocessor-definitions.md)编译器选项具有与使用相同的效果 **#define**预处理指令在你的文件的开头。 通过使用 /D 选项，最多可定义 30 个宏。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)