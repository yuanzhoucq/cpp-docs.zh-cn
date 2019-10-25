---
title: scanf 宽度规范
ms.date: 10/22/2019
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 54331f4150c50b084b59ac51b3f34ffe15c5b1c8
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811123"
---
# <a name="scanf-width-specification"></a>scanf 宽度规范

此信息适用于解释 `scanf` 系列函数中的格式字符串，包括 `scanf_s` 等安全版本。 这些函数通常假定将输入流划分为标记序列。 标记由空白（空格、制表符或换行符）或数值类型的自然端分隔，由第一个不能转换为数字文本的字符表示。 然而，宽度规范可能用于在标记的自然末尾之前停止输入分析。

宽度规范由 `%` 和类型字段说明符之间的字符组成，其中可能包括名为宽度字段的正整数以及一个或多个表示字段大小的字符，这些字符还可能被视为字段类型的修饰符，例如指示整数类型是 **short** 还是 **long**。 此类字符称为大小前缀。

## <a name="the-width-field"></a>宽度字段

*Width*字段是一个正整数，用于控制为该字段读取的最大字符数。 在相应的 `argument`中，不能转换和存储超过*宽度*字符。 如果在达到*宽度*之前不能根据给定格式转换空格字符或字符，则可能读取少于*宽度*的字符。

宽度规范是单独的，不同于这些函数的安全版本（例如 `scanf_s`、`wscanf_s`等）所需的缓冲区大小参数。 在以下示例中，宽度规范为 20，这表示从输入流中最多可读取 20 个字符。 缓冲区长度为 21，其中包括用于可能 20 个字符以及 null 终止符的空间：

```C
char str[21];
scanf_s("%20s", str, 21);
```

如果未使用*width*字段，`scanf_s` 会尝试将整个标记读取到字符串中。 如果指定的大小不足以容纳整个标记，则不会向目标字符串写入任何内容。 如果指定了*width*字段，则会将令牌中的第一个*宽度*字符与 null 终止符一起写入目标字符串。

## <a name="the-size-prefix"></a>大小前缀

可选前缀**h**、 **hh**、 **l**、 **ll**、 **I64**和**l**指示 `argument` 的大小（长或短、单字节字符或宽字符，具体取决于它们修改的类型字符）。 这些格式规范字符与类型字符一起用于 `scanf` 或 `wscanf` 函数中，用以指定参数的解释，如下表所示。 类型前缀**I64**是 Microsoft 扩展，与标准 C 不兼容。[Scanf 类型字段字符](../c-runtime-library/scanf-type-field-characters.md)中的 "scanf 函数的类型字符" 表中描述了类型字符及其含义。

> [!NOTE]
> **H**、 **l**和**l**前缀是 Microsoft 扩展，与**char**类型的数据一起使用。

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Scanf 和 wscanf 格式类型说明符的大小前缀

|若要指定|使用前缀|及类型说明符|
|----------------|----------------|-------------------------|
|**双精度**|**l**|**e**、**E**、**f**、**g** 或 **G**|
|**long double**（与 double 相同）|**L**|**e**、**E**、**f**、**g** 或 **G**|
|**long int**|**l**|**d**、**i**、**o**、**x** 或 **X**|
|**long unsigned int**|**l**|**u**|
|**long long**|**ll**|**d**、**i**、**o**、**x** 或 **X**|
|**short int**|**h**|**d**、**i**、**o**、**x** 或 **X**|
|**short unsigned int**|**h**|**u**|
|**char**|**hh**|**d**、**i**、**o**、**x** 或 **X**|
|**unsigned char**|**hh**|**u**|
|**int64**|**I64**|**d**、**i**、**o**、**u**、**x** 或 **X**|
|含 `scanf` 的单字节字符|**h**|**c** 或 **C**|
|含 `wscanf` 的单字节字符|**h**|**c** 或 **C**|
|含 `scanf` 的宽字符|**l**|**c** 或 **C**|
|含 `wscanf` 的宽字符|**l**|**c** 或 **C**|
|带有 `scanf` 的单字节字符串|**h**|**s** 或 **S**|
|带有 `wscanf` 的单字节字符串|**h**|**s** 或 **S**|
|带 `scanf` 的宽字符字符串|**l**|**s** 或 **S**|
|带 `wscanf` 的宽字符字符串|**l**|**s** 或 **S**|

以下是 **h** 和 **l** 与 `scanf_s` 函数和 `wscanf_s` 函数结合使用的示例：

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

如果在 `scanf` 系列中使用了不安全的函数，则省略表示先前参数的缓冲区长度的大小参数。

## <a name="reading-undelimited-strings"></a>读取 get-content 字符串

若要读取未由空白字符分隔的字符串，可将括号 ( **[ ]** ) 中的字符集替换为 **s**（字符串）类型字符。 括号中的字符集称为*控制字符串*。 相应的输入字段将读取到控制字符串中未显示的第一个字符。 如果字符集中的第一个字符是插入符号 ( **^** )，则效果相反：输入字段一直读取到字符集其余部分中显示的第一个字符。

**% [A-z]** 和 **% [z-a]** 均被解释为等于 **% [abcde...z .。。z]** 。 这是一个常见的 `scanf` 函数扩展，但标准 C 不需要此扩展。

## <a name="reading-unterminated-strings"></a>读取未终止的字符串

若要在不存储终止 null 字符（"\ 0"）的情况下存储字符串，请使用规范 `%Nc`，其中*N*是十进制整数。 在这种情况下，**c** 类型字符表示自变量指向字符数组。 接下来的*N*个字符将从输入流读取到指定位置，并且不追加 null 字符（' \ 0 '）。 如果未指定*N* ，则其默认值为1。

## <a name="when-scanf-stops-reading-a-field"></a>当 scanf 停止读取字段时

`scanf` 函数逐个字符地扫描每个输入字段。 由于以下原因之一，它可能会在到达空格字符之前停止读取特定输入字段：

- 已达到指定宽度。

- 下一个字符无法按指定进行转换。

- 下一个字符与它应匹配的控件字符串中的字符冲突。

- 下一个字符没有在给定字符集中出现。

无论什么原因，当 `scanf` 函数停止读取输入字段时，下一个输入字段都被视为从第一个未读取的字符处开始。 冲突字符（如果有）被视为未读取。 它是下一个输入字段的第一个字符，或输入流上后续读取操作中的第一个字符。

## <a name="see-also"></a>请参阅

[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[格式规范字段：scanf 和 wscanf 函数](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf 类型字段字符](../c-runtime-library/scanf-type-field-characters.md)<br/>
