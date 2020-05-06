---
title: 多字节和宽字符
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
ms.openlocfilehash: 0d573fac938f5e4d62c99c8cd6e676b96123a0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232909"
---
# <a name="multibyte-and-wide-characters"></a>多字节和宽字符

多字节字符是由一个或多个字节的序列构成的字符。 每个字节序列表示扩展字符集中的单个字符。 多字节字符用于字符集（如日文汉字）中。

宽字符是宽度始终为 16 位的多语言字符代码。 字符常量的类型是 `char`；对于宽字符，该类型是 `wchar_t`。 由于宽字符始终具有固定大小，因此使用宽字符集可以简化使用国际字符集进行的编程。

宽字符串文本 `L"hello"` 将成为类型为 `wchar_t` 的六个整数的数组。

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Unicode 规范是宽字符的规范。 用于多字节和宽字符之间的转换的运行库例程包括 `mbstowcs`、`mbtowc`、`wcstombs` 和 `wctomb`。

## <a name="see-also"></a>请参阅

[C 标识符](../c-language/c-identifiers.md)
