---
title: C 标识符
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: d68eb690a19f57555d9d757a2f058692ea1a40c3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223741"
---
# <a name="c-identifiers"></a>C 标识符

“Identifiers”或“symbols”是您为程序中的变量、类型、函数和标签提供的名称。 标识符名称在拼写和大小写上必须与任何关键字都不同。 不能将关键词（C 或 Microsoft）用作标识符；将它们保留以用于特殊用途。 通过在变量、类型或函数的声明中指定标识符来创建标识符。 在此示例中，`result` 是整型变量的标识符，`main` 和 `printf` 是函数的标识符名称。

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

声明后，您可在以后的程序语句中使用标识符来引用关联值。

可以在 `goto` 语句中使用一种特殊的标识符，称为“语句标签”。 （[声明和类型](../c-language/declarations-and-types.md)中介绍了声明，[goto 和标记语句](../c-language/goto-and-labeled-statements-c.md)中介绍了语句标签。）

## <a name="syntax"></a>语法

identifier  ：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

*nondigit*：以下之一：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **_ a b c d e f g h i j k l mn o p q r s t u v w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L MN O P Q R S T U V W X Y Z**

*digit*：以下之一：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;0 1 2 3 4 5 6 7 8 9

标识符名称的第一个字符必须是 `nondigit`（即，第一个字符必须是下划线、大写字母或小写字母）。 ANSI 允许外部标识符名称包含 6 个有效字符，内部（一个函数中）标识符名称包含 31 个有效字符。 外部标识符（在全局范围声明的或使用存储类 `extern` 声明的标识符）可能会受到额外的命名限制，因为这些标识符必须由其他软件（如链接器）处理。

**Microsoft 专用**

尽管 ANSI 允许外部标识符名称包含 6 个有效字符，内部标识符（在一个函数内）名称包含 31 个有效字符，但 Microsoft C 编译器允许内部或外部标识符名称包含 247 个字符。 如果您不担心 ANSI 兼容性，则可使用 /H（限制外部名称的长度）选项将此默认值修改为更小或更大的数字。

**结束 Microsoft 专用**

C 编译器会将大写和小写字母视为不同的字符。 利用此功能（称为“区分大小写”），您可以创建拼写相同但一个或多个字母的大小写不同的不同标识符。 例如，下列每个标识符都是唯一的：

```
add
ADD
Add
aDD
```

**Microsoft 专用**

请勿为标识符选择以两条下划线开头或者以一条下划线后跟一个大写字母开头的名称。 ANSI C 标准允许保留以这些字符组合开头的标识符名称以供编译器使用。 不应将一条下划线和一个小写字母作为前两个字母来命名具有五级范围的标识符。 以这些字符开头的标识符名称也将保留。 按照约定，Microsoft 使用下划线和大写字母作为宏名称的开头，并使用双下划线作为 Microsoft 特定关键字名称的开头。 若要避免任何命名冲突，请始终选择不是以一条或两条下划线开头的标识符名称，或选择以一条下划线后跟一个大写字母开头的名称。

**结束 Microsoft 专用**

下面是符合 ANSI 或 Microsoft 命名限制的有效标识符的示例：

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Microsoft 专用**

尽管默认情况下源文件中的标识符区分大小写，但对象文件中的符号不区分大小写。 Microsoft C 将编译单元中的标识符视为区分大小写。

Microsoft 链接器区分大小写。 您必须根据情况一致地指定所有标识符。

“源字符集”是可能出现在源文件中的合法字符集。 对于 Microsoft C，源集是标准 ASCII 字符集。 源字符集和执行字符集包含用作转义序列的 ASCII 字符。 有关执行字符集的信息，请参阅[字符常量](../c-language/c-character-constants.md)。

**结束 Microsoft 专用**

标识符具有“范围”（在程序中发现标识符的区域）和“链接”（确定其他范围中的同一名称是否引用同一标识符）。 [生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)中介绍了这些主题。

## <a name="see-also"></a>请参阅

[C 的元素](../c-language/elements-of-c.md)
