---
title: 区域设置和代码页
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: 5821048363d92911f2902a580cb11f5b349f5e7c
ms.sourcegitcommit: 4f15b69e35dd112001b24fe9dc836dd5d6902465
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474071"
---
# <a name="locales-and-code-pages"></a>区域设置和代码页

区域设置 ID 反映特定地理区域的本地约定和语言。 可能有一个以上的国家/地区说某种特定的语言，例如，巴西和葡萄牙都说葡萄牙语。 反之，一个国家/地区可能有一种以上的官方语言。 例如，加拿大有两种语言：英语和法语。 因此，加拿大有两个不同的区域设置：加拿大英语和加拿大法语。 一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。

语言确定文本和数据的格式约定，而国家/地区则确定本地约定。 每种语言都有一个由代码页表示的唯一映射，其中包括字母表中的字符（如标点符号和数字）。 代码页是一个字符集，并与语言相关。 因此，[区域设置](../c-runtime-library/locale.md)是语言、国家/地区和代码页的独特组合。 可以在运行时通过调用[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)函数更改区域设置和代码页设置。

不同的语言可能使用不同的代码页。 例如，ANSI 代码页1252用于英语和大多数欧洲语言，ANSI 代码页932用于日本汉字。 几乎所有代码页都共享最小128个字符（0x00 到0x7F）的 ASCII 字符集。

任何单字节代码页都可以在表中表示（包含256条目），以将字节值映射为字符（包括数字和标点符号）或字形。 任何多字节代码页也可以表示为字节的双字节值的超大型表（包含64K 条目）。 但实际上，它通常表示为第一个256（单字节）字符的表和双字节值的范围。

有关代码页的详细信息，请参见 [Code Pages](../c-runtime-library/code-pages.md)。

C 运行时库具有两种类型的内部代码页：区域设置和多字节。 可以在程序执行期间更改当前代码页（请参阅[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)和[_setmbcp](../c-runtime-library/reference/setmbcp.md)函数的文档）。 此外，运行时库可能会获取并使用操作系统代码页的值，它在程序执行期间是常量。

区域设置代码页发生更改时，与区域设置相关的函数集的行为将更改为所选代码页所指示的行为。 默认情况下，所有与区域设置相关的函数会开始执行，并使用 "C" 区域设置唯一的区域设置代码页。 您可以通过调用 `setlocale` 函数来更改内部区域设置代码页（以及其他特定于区域设置的属性）。 对 `setlocale`（LC_ALL，""）的调用会将区域设置设置为操作系统用户区域设置所指示的区域设置。

同样，当多字节代码页发生更改时，多字节函数的行为将更改为所选代码页所指示的。 默认情况下，所有多字节函数开始执行，其中包含与操作系统的默认代码页对应的多字节代码页。 可以通过调用 `_setmbcp` 函数来更改内部多字节代码页。

C 运行时函数 `setlocale` 设置、更改或查询当前程序的部分或全部区域设置信息。 [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)例程是 `setlocale`的宽字符版本;`_wsetlocale` 的参数和返回值都是宽字符字符串。

## <a name="see-also"></a>另请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[字符集可迁移性的好处](../text/benefits-of-character-set-portability.md)
