---
title: scanf 宽度规范
ms.date: 11/04/2016
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: e4608d46664dad3e04d37a82368cc6e7173106f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445157"
---
# <a name="scanf-width-specification"></a>scanf 宽度规范

此信息适用于解释 `scanf` 系列函数中的格式字符串，包括 `scanf_s` 等安全版本。 这些函数通常假定将输入流划分为标记序列。 标记通过空白字符（空格、制表符或换行）进行分隔，或者在数值类型的情况下，按无法转换为数值文本的第一个字符所示由数值数据类型的自然末尾进行分隔。 然而，宽度规范可能用于在标记的自然末尾之前停止输入分析。

宽度规范由 `%` 和类型字段说明符之间的字符组成，其中可能包括名为宽度字段的正整数以及一个或多个表示字段大小的字符，这些字符还可能被视为字段类型的修饰符，例如指示整数类型是 **short** 还是 **long**。 此类字符称为大小前缀。

## <a name="the-width-field"></a>宽度字段

“宽度”字段是十进制正整数，用于控制为该字段读取的字符最大数量。 不超过宽度的字符会转换并存储在相应的 `argument` 中。 如果达到宽度之前出现空白字符（空格、制表符或换行）或根据给定格式不能转换的字符，则可能读取少于宽度的字符。

宽度规范是单独的，且不同于这些函数的安全版本（即 `scanf_s`、`wscanf_s` 等）所需的缓冲区大小参数。 在以下示例中，宽度规范为 20，这表示从输入流中最多可读取 20 个字符。 缓冲区长度为 21，其中包括用于可能 20 个字符以及 null 终止符的空间：

```C
char str[21];
scanf_s("%20s", str, 21);
```

如果未使用宽度字段，则 `scanf_s` 会尝试将整个标记读取到字符串中。 如果指定的大小不足以容纳整个标记，则不会向目标字符串写入任何内容。 如果指定了宽度字段，则将标记中的第一个宽度字符与 null 终止符一起写入目标字符串。

## <a name="the-size-prefix"></a>大小前缀

可选前缀 **h**、**l**、**ll**、**I64** 和 **L** 指示 `argument` 的大小（long 或 short、单字节字符或宽字符，具体取决于它们修饰的类型字符）。 这些格式规范字符与类型字符一起用于 `scanf` 或 `wscanf` 函数中，用以指定参数的解释，如下表所示。 类型前缀 **I64** 是 Microsoft 扩展，与 ANSI 不兼容。 有关类型字符及其含义的描述，请参阅 [scanf 类型字段字符](../c-runtime-library/scanf-type-field-characters.md)中的“scanf 函数的类型字符”表。

> [!NOTE]
> 与类型为 `char` 的数据一起使用时，**h**、**l** 和 **L** 前缀是 Microsoft 扩展。

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>scanf 和 wscanf 格式类型说明符的大小前缀

|若要指定|使用前缀|及类型说明符|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**、**E**、**f**、**g** 或 **G**|
|**long double**（与 double 相同）|**L**|**e**、**E**、**f**、**g** 或 **G**|
|**long int**|**l**|**d**、**i**、**o**、**x** 或 **X**|
|**long unsigned int**|**l**|**u**|
|**long long**|**ll**|**d**、**i**、**o**、**x** 或 **X**|
|`short int`|**h**|**d**、**i**、**o**、**x** 或 **X**|
|**short unsigned int**|**h**|**u**|
|__**int64**|**I64**|**d**、**i**、**o**、**u**、**x** 或 **X**|
|含 `scanf` 的单字节字符|**h**|**c** 或 **C**|
|含 `wscanf` 的单字节字符|**h**|**c** 或 **C**|
|含 `scanf` 的宽字符|**l**|**c** 或 **C**|
|含 `wscanf` 的宽字符|**l**|**c** 或 **C**|
|含 `scanf` 的单字节字符串|**h**|**s** 或 **S**|
|含 `wscanf` 的单字节字符串|**h**|**s** 或 **S**|
|含 `scanf` 的宽字符字符串|**l**|**s** 或 **S**|
|含 `wscanf` 的宽字符字符串|**l**|**s** 或 **S**|

以下是 **h** 和 **l** 与 `scanf_s` 函数和 `wscanf_s` 函数结合使用的示例：

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

如果在 `scanf` 系列中使用了不安全的函数，则省略表示先前参数的缓冲区长度的大小参数。

## <a name="reading-undelimited-strings"></a>读取未分隔的字符串

若要读取未由空白字符分隔的字符串，可将括号 (**[ ]**) 中的字符集替换为 **s**（字符串）类型字符。 括号中的字符集称为控制字符串。 相应的输入字段一直读取到控制字符串中未显示的第一个字符。 如果字符集中的第一个字符是插入符号 (**^**)，则效果相反：输入字段一直读取到字符集其余部分中显示的第一个字符。

请注意，**%[a-z]** 和 **%[z-a]** 解释为与 **%[abcde...z]** 等同。 这是一个常见的 `scanf` 函数扩展，但请注意，ANSI 标准并不需要此扩展。

## <a name="reading-unterminated-strings"></a>读取未终止的字符串

若要在不保存终止空字符 ('\0') 的情况下保存字符串，请使用规范 %<em>n</em>c，其中 n 是十进制整数。 在这种情况下，**c** 类型字符表示自变量指向字符数组。 接下来的 *n* 字符从输入流读取到指定位置，不附加任何空字符 ('\0')。 如果 *n* 未指定，则其默认值为 1。

## <a name="when-scanf-stops-reading-a-field"></a>当 scanf 停止读取字段时

`scanf` 函数逐个字符地扫描每个输入字段。 由于各种原因，可能在达到空格字符之前停止读取特定输入字段：

- 已达到指定宽度。

- 下一个字符无法按指定进行转换。

- 下一个字符与应该匹配的控制字符串中的字符冲突。

- 下一个字符没有在给定字符集中出现。

无论什么原因，当 `scanf` 函数停止读取输入字段时，下一个输入字段都被视为从第一个未读取的字符处开始。 冲突字符（如果有）被视为未读取，且是下一个输入字段的第一个字符或输入流上后续读取操作中的第一个字符。

## <a name="see-also"></a>请参阅

[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[格式规范字段：scanf 和 wscanf 函数](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf 类型字段字符](../c-runtime-library/scanf-type-field-characters.md)<br/>
