---
title: '#define 指令 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: b72e2468b9e9984237c81f5cdb3c5691fe95cbd0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216277"
---
# <a name="define-directive-cc"></a>#define 指令 (C/C++)

**#Define**创建一个宏, 该*宏*是标识符或参数化标识符与标记字符串的关联。 在定义宏之后，编译器可用标记字符串替换源文件中标识符的每个匹配项。

## <a name="syntax"></a>语法

> **#define** *标识符* *标记-字符串*<sub>opt</sub>\
> **#define** *标识符* **(** *标识符*<sub>opt</sub> **,** ... **,** *标识符*<sub>opt</sub> **)** *令牌字符串*<sub>选择</sub>

## <a name="remarks"></a>备注

**#Define**指令导致编译器替换源文件中*标识符*的每个匹配项的*标记字符串*。 仅当*标识符*形成标记时, 才会将其替换。 也就是说, 如果*标识符*出现在注释、字符串中或较长的标识符中, 则不会将其替换。 有关详细信息, 请参阅[标记](../cpp/tokens-cpp.md)。

*标记字符串*参数由一系列标记 (如关键字、常量或完整语句) 组成。 一个或多个空白字符必须与*标识符*分隔*标记字符串*。 此空白不会被视为替换文本的一部分，也不是跟在文本最后一个标记后面的任何空白。

不带*标记字符串*的不会从源文件中删除*标识符。* `#define` *标识符*保持定义, 并可以使用`#if defined`和`#ifdef`指令进行测试。

第二种语法形式定义一个带有参数的类似函数的宏。 此形式接受必须出现在括号内的参数的可选列表。 定义宏后,*标识符*的每个后续匹配项 (*标识符*<sub>opt</sub>, ...,*标识符*<sub>opt</sub> ) 都将替换为具有实际参数的*令牌字符串*参数的版本替换形参。

形参名称出现在*标记字符串*中, 用于标记替换实际值的位置。 每个参数名称在*标记字符串*中可以出现多次, 并且名称可以按任意顺序出现。 调用中的参数数目必须与宏定义中的参数数目一致。 对括号的自由使用将确保正确解释复杂的实参。

将用逗号分隔列表中的形参。 列表中的每个名称必须是唯一的，并且列表必须用括号括起。 不能有空格分隔*标识符*和左括号。 使用行串连-将反斜杠 (`\`) 紧靠在换行符前 () 放置在多个源行的长指令上。 形参名称的范围扩展到结束*标记字符串*的新行。

使用第二种语法形式定义宏之后，后面跟有自变量列表的后续文本实例指示一个宏调用。 在源文件中的*标识符*实例之后的实际参数与宏定义中的相应形参匹配。 不在字符串化 ( `#`)、charizing (`#@`) 或标记粘贴 (`##`) 运算符前面、但后面`##`不是运算符的每个形参都将替换为相应的实参。 实际自变量中的所有宏都将在指令替换形式参数之前展开。 ([预处理器运算符](../preprocessor/preprocessor-operators.md)中介绍了运算符。)

以下包含参数的宏的示例演示了 **#define**语法的第二种形式:

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

有副作用的参数有时会导致宏产生意外的结果。 给定的形参可在*标记字符串*中多次出现。 如果将该形参替换为有副作用的表达式，则可能多次计算该表达式及其副作用。 (请参阅[标记粘贴运算符 (# #)](../preprocessor/token-pasting-operator-hash-hash.md)下的示例。)

`#undef` 指令促使忘记标识符的预处理器定义。 有关详细信息, 请参阅[#undef 指令](../preprocessor/hash-undef-directive-c-cpp.md)。

如果要定义的宏的名称出现在*标记字符串*中 (即使是另一个宏扩展的结果), 则它不会展开。

除非第二个标记序列与第一个标记序列相同, 否则, 具有相同名称的宏的第二个 **#define**将生成一个警告。

**Microsoft 专用**

如果新定义在语法上与原始定义相同，则 Microsoft C/C++ 允许您重新定义宏。 换言之，这两个定义可以具有不同的参数名称。 此行为与 ANSI C 不同, 后者要求两个定义在词法上是相同的。

例如，下面两个宏除参数名称外完全相同。 ANSI C 不允许进行此类重定义, 但 Microsoft CC++ /编译它时没有错误。

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

此示例演示了 **#define**指令:

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

计算结果为280。

**Microsoft 专用**

使用[/d](../build/reference/d-preprocessor-definitions.md)编译器选项定义宏和常量具有与在文件开头使用 **#define**预处理指令相同的效果。 通过使用 /D 选项，最多可定义 30 个宏。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
