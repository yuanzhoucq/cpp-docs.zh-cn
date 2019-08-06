---
title: 字符串化运算符 (#)
ms.date: 11/04/2016
f1_keywords:
- '#'
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
ms.openlocfilehash: d90d07c8f3cce6c443be0eb994db494746c00fcc
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711143"
---
# <a name="stringizing-operator-"></a>字符串化运算符 (#)

数字符号或 "字符串化" 运算符 ( **#** ) 将宏参数转换为字符串文本, 而无需展开参数定义。 它只用于采用参数的宏。 如果它在宏定义中位于形式参数之前，则由宏调用传递的实际自变量将用引号引起来并被视为字符串。 字符串随后替换宏定义中的字符串化运算符和形参的组合的每个匹配项。

> [!NOTE]
> 不再支持对 ANSI C 标准的 Microsoft C（6.0 版和早期版本）扩展，该扩展之前扩展了出现在字符串和字符常量内的扩展的宏形式自变量。 应使用字符串化 ( **#** ) 运算符重写依赖于此扩展的代码。

在实参的第一个标记前且紧跟实参的最后一个标记的空格将被忽略。 在生成的字符串中，将自变量标记之间的所有空格减少到单一空格。 因此，如果注释出现在自变量的两个标记之间，则将其减少为单个空格。 生成的字符串自动与仅由空格分隔的任何相邻的字符串连接。

此外, 如果参数中包含的字符在字符串中使用时通常需要转义序列 (例如, 引号 ( **"** ) 或反斜杠 ( **\\** ) 字符), 则将自动插入必要的转义反斜杠在该字符之前。

当 Visual C++字符串化运算符与包含转义序列的字符串一起使用时, 它的行为不正确。 在这种情况下, 编译器将生成[编译器错误 C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md)。

## <a name="examples"></a>示例

以下示例显示一个包含字符串化运算符的宏定义和一个调用该宏的主函数：

```cpp
// stringizer.cpp
#include <stdio.h>
#define stringer( x ) printf_s( #x "\n" )
int main() {
   stringer( In quotes in the printf function call );
   stringer( "In quotes when printed to the screen" );
   stringer( "This: \"  prints an escaped double quote" );
}
```

在预处理过程中将展开宏,从而生成以下代码:`stringer`

```cpp
int main() {
   printf_s( "In quotes in the printf function call" "\n" );
   printf_s( "\"In quotes when printed to the screen\"" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
}
```

```Output
In quotes in the printf function call
"In quotes when printed to the screen"
"This: \"  prints an escaped double quote"
```

以下示例说明如何扩展宏参数：

```cpp
// stringizer_2.cpp
// compile with: /E
#define F abc
#define B def
#define FB(arg) #arg
#define FB1(arg) FB(arg)
FB(F B)
FB1(F B)
```

## <a name="see-also"></a>请参阅

[预处理器运算符](../preprocessor/preprocessor-operators.md)
