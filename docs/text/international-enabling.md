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
ms.openlocfilehash: 22f2dba49e894e93cb6791d76a65730f3269199e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748003"
---
# <a name="international-enabling"></a>国际支持

大多数传统的 C 和 c + + 代码作出有关字符和字符串操作不起作用于国际应用程序。 MFC 和运行时库支持 Unicode 或 MBCS，而是仍让您做什么工作。 引导您，本部分介绍在 Visual c + + 中的"国际支持"的含义：

- Unicode 和 MBCS MFC 函数参数列表中的可移植数据类型通过启用和返回类型。 这些类型有条件地定义以适当的方式，具体取决于是否在生成定义的符号`_UNICODE`或符号`_MBCS`（这意味着 DBCS）。 应用程序后，这两个符号取决于你的生成定义自动链接 MFC 库的不同变体。

- 类库代码使用可移植运行时函数和其他方法来确保正确的 Unicode 或 MBCS 行为。

- 仍必须在代码中处理某些种类的国际化任务：

   - 使用相同的可移植运行时函数，使 MFC 在这两种环境下可移植。

   - 使文本字符串和字符在任一环境，可移植使用`_T`宏。 有关详细信息，请参阅[tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。

   - 分析下 MBCS 字符串时，请采取预防措施。 在 Unicode 下不需要这些预防措施。 有关详细信息，请参阅[MBCS 编程提示](../text/mbcs-programming-tips.md)。

   - 请注意，如果在应用程序中混合使用 ANSI （8 位） 和 Unicode （16 位） 字符。 可以使用应用程序的某些部分中的 ANSI 字符和 Unicode 字符在其他用例，但您不能在相同的字符串中混合使用它们。

   - 请不要在应用程序中的硬编码字符串。 相反，通过使它们 STRINGTABLE 资源将其添加到应用程序的.rc 文件。 你的应用程序然后可以本地化而无需更改源代码或重新编译。 STRINGTABLE 资源有关的详细信息，请参阅[字符串编辑器](../windows/string-editor.md)。

> [!NOTE]
>  欧洲和 MBCS 字符集有一些字符，如带重音符的字母，与大于 0x80 字符代码。 因为大多数代码使用带符号的字符时，这些字符大于 0x80 是带符号扩展时转换为**int**。这是因为符号扩展的字符为负值，则索引将超出数组的数组索引的问题。 使用 MBCS，如日语语言也是唯一的。 由于字符可能包含 1 或 2 个字节，应始终在同一时间处理两个字节。

## <a name="see-also"></a>请参阅

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[国际化策略](../text/internationalization-strategies.md)
