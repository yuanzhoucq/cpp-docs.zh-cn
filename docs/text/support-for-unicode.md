---
title: 支持 Unicode
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: 0b61407920a0ce35a1c6a8466458736e983e271e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168559"
---
# <a name="support-for-unicode"></a>支持 Unicode

Unicode 是支持所有字符集（包括不能用单字节表示的字符集）的规范。  如果要对国际市场进行编程，建议使用 Unicode 或[多字节字符集](../text/support-for-multibyte-character-sets-mbcss.md)（MBCS）。 或者编写程序代码，以便可以通过更改开关来生成。

宽字符是双字节多语言字符代码。 成千上万个字符（包括技术符号和特殊的发布字符）可根据 Unicode 规范（包括技术符号和特殊的发布字符）用使用 UTF-16。 使用 Unicode 代理项对功能，只能在 Unicode 对中表示不能用一个宽字符表示的字符。 由于几乎每个字符在单个16位宽字符中以 UTF-16 表示，因此使用宽字符可简化使用国际字符集进行的编程。 使用 UTF-16LE （对于小字节序）进行编码的宽字符是 Windows 的本机字符格式。

宽字符串表示为一个 `wchar_t[]` 数组，由 `wchar_t*` 指针指向它。 通过使用字母 L 作为该字符的前缀，可将任何 ASCII 字符表示为宽字符。 例如，L'\0' 是（16 位）NULL 终止宽字符。 同样，通过使用字母 L 作为 ASCII 文本的前缀 (L"Hello")，可将任何 ASCII 字符串文本表示为宽字符字符串。

通常，宽字符在内存中占用的空间比多字节字符多，但处理速度更快。 此外，在多字节编码中一次只能表示一个区域设置，而世界上的所有字符集同时由 Unicode 表示形式表示。

MFC 框架完全支持 Unicode，MFC 通过使用可移植的宏来实现对 Unicode 的支持，如下表所示。

## <a name="portable-data-types-in-mfc"></a>MFC 中的可移植数据类型

|不可移植的数据类型|替换为此宏|
|-----------------------------|----------------------------|
|`char`、`wchar_t`|`_TCHAR`|
|`char*`，`LPSTR` （Win32 数据类型），`LPWSTR`|`LPTSTR`|
|`const char*`，`LPCSTR` （Win32 数据类型），`LPCWSTR`|`LPCTSTR`|

类 `CString` 使用 `_TCHAR` 作为其基，并提供用于轻松转换的构造函数和运算符。 通过使用与用于处理 Windows ANSI 字符集相同的逻辑，可编写 Unicode 的大多数字符串操作，但基本操作单位是 16 位字符，而非 8 位字节。 与使用多字节字符集不同，不必（也不应）将 Unicode 字符视为两个不同的字节。 但是，您必须处理由代理项对宽字符表示的单个字符。 通常，不要编写假定字符串长度与它所包含的字符数（无论是否为窄或宽）相同的代码。

## <a name="what-do-you-want-to-do"></a>您希望做什么？

- [使用 MFC Unicode 和多字节字符集（MBCS）支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [在我的程序中启用 Unicode](../text/international-enabling.md)

- [在我的程序中启用 Unicode 和 MBCS](../text/internationalization-strategies.md)

- [使用 Unicode 创建国际化程序](../text/unicode-programming-summary.md)

- [了解 Unicode 的优点](../text/benefits-of-character-set-portability.md)

- [使用 wmain 以便我可以将宽字符参数传递给我的程序](../text/support-for-using-wmain.md)

- [请参阅 Unicode 编程摘要](../text/unicode-programming-summary.md)

- [了解用于字节宽度可移植性的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>另请参阅

[文本和字符串](../text/text-and-strings-in-visual-cpp.md)<br/>
[支持使用 wmain](../text/support-for-using-wmain.md)
