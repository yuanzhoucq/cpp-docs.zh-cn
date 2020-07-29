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
ms.openlocfilehash: ff0fb4102a0453b900b5b406739492a9420a5b07
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228084"
---
# <a name="international-enabling"></a>国际支持

大多数传统 C 和 c + + 代码都假设了对于国际应用程序而言不太好的字符和字符串操作。 虽然 MFC 和运行时库都支持 Unicode 或 MBCS，但仍有适合你的工作。 为指导您，本部分说明了 Visual C++ 中的 "国际启用" 的含义：

- Unicode 和 MBCS 通过 MFC 函数参数列表和返回类型中的可移植数据类型启用。 这些类型根据您的生成是否定义符号 `_UNICODE` 或符号 `_MBCS` （这意味着 DBCS），按适当方式定义。 MFC 库的不同变体自动与您的应用程序链接，具体取决于您的生成所定义的两个符号中的哪一个。

- 类库代码使用可移植运行时函数和其他方法来确保 Unicode 或 MBCS 行为的正确性。

- 你仍必须在代码中处理某些类型的国际化任务：

  - 使用相同的可移植运行时函数，使 MFC 在任一环境下可移植。

  - 使用宏在任一环境下可移植文本字符串和字符 `_T` 。 有关详细信息，请参阅[tchar 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。

  - 在 MBCS 下分析字符串时，请采取预防措施。 Unicode 不需要这些预防措施。 有关详细信息，请参阅[MBCS 编程提示](../text/mbcs-programming-tips.md)。

  - 请注意，在应用程序中混合使用 ANSI （8位）和 Unicode （16位）字符。 可以在程序的某些部分使用 ANSI 字符，在其他部分中使用 Unicode 字符，但不能在同一字符串中混合使用。

  - 不要对应用程序中的字符串进行硬编码。 相反，请将它们添加到应用程序的 .rc 文件，使其 STRINGTABLE 资源。 然后，可以对应用程序进行本地化，无需更改或重新编译源代码。 有关 STRINGTABLE 资源的详细信息，请参阅[字符串编辑器](../windows/string-editor.md)。

> [!NOTE]
> 欧洲和 MBCS 字符集包含一些字符（如重音字母），字符代码大于0x80。 由于大多数代码使用带符号的字符，因此在转换为时，这些大于0x80 的字符将进行符号扩展 **`int`** 。 这对于数组索引是一个问题，因为符号扩展字符（负）是数组外的索引。 使用 MBCS 的语言（如日语）也是唯一的。 因为某个字符可能包含1个或2个字节，所以应始终同时处理这两个字节。

## <a name="see-also"></a>另请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[国际化策略](../text/internationalization-strategies.md)
