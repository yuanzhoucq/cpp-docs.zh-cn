---
title: 国际支持
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375805"
---
# <a name="international-enabling"></a>国际支持

大多数传统的 C 和 C++ 代码对字符和字符串操作做出的假设，这些假设不适用于国际应用程序。 虽然 MFC 和运行时库都支持 Unicode 或 MBCS，但仍有工作要做。 为了指导您，本节在 Visual C++ 中解释了"国际启用"的含义：

- Unicode 和 MBCS 都通过 MFC 函数参数列表和返回类型中的可移植数据类型启用。 这些类型以适当的方式有条件地定义，具体取决于生成是定义符号`_UNICODE`还是符号`_MBCS`（这意味着 DBCS）。 MFC 库的不同变体会自动与应用程序链接，具体取决于生成定义的这两个符号中的哪一个。

- 类库代码使用便携式运行时函数和其他方法来确保正确的 Unicode 或 MBCS 行为。

- 您仍必须在代码中处理某些类型的国际化任务：

  - 使用使 MFC 在任一环境下可移植的相同便携式运行时功能。

  - 使用`_T`宏使文本字符串和字符在任一环境中可移植。 有关详细信息，请参阅[tchar.h 中的通用文本映射](../text/generic-text-mappings-in-tchar-h.md)。

  - 在 MBCS 下分析字符串时采取预防措施。 在 Unicode 下不需要这些预防措施。 有关详细信息，请参阅[MBCS 编程提示](../text/mbcs-programming-tips.md)。

  - 如果将 ANSI（8 位）和 Unicode（16 位）字符混合在应用程序中，请小心。 可以在程序的某些部分使用 ANSI 字符，在另一些部分使用 Unicode 字符，但不能将它们混合在同一字符串中。

  - 不要在应用程序中硬编码字符串。 相反，通过将资源添加到应用程序的 .rc 文件中，使它们成为 STRINGTABLE 资源。 然后，可以本地化应用程序，而无需更改源代码或重新编译。 有关 STRINGTABLE 资源的详细信息，请参阅[字符串编辑器](../windows/string-editor.md)。

> [!NOTE]
> 欧洲字符集和 MBCS 字符集具有一些字符，如重音字母，字符代码大于 0x80。 由于大多数代码使用签名字符，因此这些大于 0x80 的字符在转换为**int**时将签名扩展。这是数组索引的问题，因为符号扩展字符（为负字符）在数组外部编制索引。 使用 MBCS 的语言（如日语）也是唯一的。 由于字符可能由 1 或 2 个字节组成，因此应始终同时操作两个字节。

## <a name="see-also"></a>另请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[国际化战略](../text/internationalization-strategies.md)
