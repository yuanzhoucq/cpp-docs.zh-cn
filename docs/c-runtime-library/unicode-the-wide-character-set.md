---
title: Unicode：宽字符集 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fcd1c874c1701f471026deec73ab596971d3ad4
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="unicode-the-wide-character-set"></a>Unicode：宽字符集

宽字符是双字节多语言字符代码。 在现代全球计算业内使用的任意字符（包括技术符号和特殊的发布字符），都可以根据 Unicode 规范表示为宽字符形式。 由包括 Microsoft 在内的大财团开发和维护的 Unicode 标准现在被广泛接受。

宽字符的类型为 wchar_t。 宽字符字符串表示为一个 wchar_t[] 数组并由 `wchar_t*` 指针指向它。 可以通过在字符前放置字母 L 作为前缀来将任何 ASCII 字符表示为宽字符形式。 例如，L'\0' 是（16 位）null 终止宽字符。 同样，您可以通过在 ASCII 文本前放置字母 L 作为前缀 (L"Hello") 来将任何 ASCII 字符串文本表示为宽字符串文本形式。

通常，宽字符在内存中占用的空间比多字节字符多，但处理速度更快。 另外，在多字节编码中一次只能表示一个区域设置，而世界上的所有字符集可以同时以 Unicode 表示形式表示。

## <a name="see-also"></a>请参阅

[国际化](../c-runtime-library/internationalization.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
