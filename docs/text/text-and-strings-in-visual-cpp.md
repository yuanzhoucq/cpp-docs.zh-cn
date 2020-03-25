---
title: Visual C++ 中的文本和字符串
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: 80b7139996fddc82b206828d4a036922fa1446d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167597"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ 中的文本和字符串

开发面向国际市场的应用程序的一个重要方面是本地字符集的充分表示。 ASCII 字符集定义0x00 到0x7F 范围内的字符。 还有其他字符集（主要为欧洲），用于定义0x00 到0x7F 范围内与 ASCII 字符集相同的字符，还可以定义从0x80 到0xFF 的扩展字符集。 因此，8位的单字节字符集（SBCS）足以表示 ASCII 字符集以及许多欧洲语言的字符集，这一点非常好。 但是，一些非欧洲字符集（如日本汉字）包含的字符数多于单字节编码方案可表示的字符数，因此需要多字节字符集（MBCS）编码。

## <a name="in-this-section"></a>本节内容

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
讨论对C++ UNICODE 和 MBCS 编程的可视化支持。

[支持 Unicode](../text/support-for-unicode.md)<br/>
描述 Unicode，它是一种支持所有字符集（包括无法用单字节表示的字符集）的规范。

[支持多字节字符集（MBCS）](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
讨论 MBCS，它是一种替代 Unicode 的替代方法，用于支持无法用单字节表示的字符集，如日语和中文。

[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)<br/>
为许多数据类型、例程和其他对象提供特定于 Microsoft 的一般文本映射。

[如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)<br/>
演示如何将各种视觉C++字符串类型转换为其他字符串。

## <a name="related-sections"></a>相关章节

[国际化](../c-runtime-library/internationalization.md)<br/>
讨论 C 运行时库中的国际支持。

[国际示例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International)<br/>
提供指向演示视觉对象C++的示例的链接。

[语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
提供 C 运行时库中的语言和国家/地区字符串。
