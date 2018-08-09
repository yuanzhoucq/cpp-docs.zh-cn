---
title: 有关 Unicode 的支持 |Microsoft Docs
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53c71e1efad109daea689725ebbbb7dd9b100d30
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020164"
---
# <a name="support-for-unicode"></a>支持 Unicode

Unicode 是支持所有字符集，包括那些不能表示仅为一个字节 （即，其中的大多数） 中的规范。 如果为国际市场编程时，我们建议你使用 Unicode 或[多字节字符集](../text/support-for-multibyte-character-sets-mbcss.md)(MBCS)，或对程序进行编码，以便能够通过更改开关来生成。

宽字符是双字节多语言字符代码。 可以根据 Unicode 规范为单个范围表示数以万计的字符，其中包含几乎所有使用的字符在现代全球，计算包括技术符号和特殊的发布字符，字符编码使用 utf-16。 通过使用 Unicode 代理项对功能，可在 Unicode 对表示不能在一个宽字符表示的字符。 由于普通用途的几乎每个字符以 utf-16 表示在单个 16 位宽字符，使用宽字符可以简化使用国际字符集进行编程。 宽字符编码 （适用于小字节序） 使用 UTF 16LE 是 Windows 的本机字符格式。

宽字符串表示为一个 `wchar_t[]` 数组，由 `wchar_t*` 指针指向它。 通过使用字母 L 作为该字符的前缀，可将任何 ASCII 字符表示为宽字符。 例如，L \0' 是终止宽 （16 位） NULL 字符。 同样，通过使用字母 L 作为 ASCII 文本的前缀 (L"Hello")，可将任何 ASCII 字符串文本表示为宽字符字符串。

通常，宽字符在内存中占用的空间比多字节字符多，但处理速度更快。 此外，只有一个区域设置可以表示多字节编码中一次，而世界中的所有字符都设置同时以 Unicode 表示形式。

MFC 框架完全支持 Unicode，MFC 通过使用可移植的宏来实现对 Unicode 的支持，如下表所示。

## <a name="portable-data-types-in-mfc"></a>MFC 中的可移植数据类型

|不可移植的数据类型|替换为此宏|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*``LPSTR` （Win32 数据类型） `LPWSTR`|`LPTSTR`|
|`const char*``LPCSTR` （Win32 数据类型） `LPCWSTR`|`LPCTSTR`|

类`CString`使用`_TCHAR`作为其基类，并提供构造函数和运算符以方便转换。 通过使用与用于处理 Windows ANSI 字符集相同的逻辑，可编写 Unicode 的大多数字符串操作，但基本操作单位是 16 位字符，而非 8 位字节。 与使用多字节字符集不同，不必（也不应）将 Unicode 字符视为两个不同的字节。 执行操作，但是，必须处理由代理项对的宽字符表示的单个字符的可能性。 一般情况下，不要编写会假定字符串的长度为相同数量的字符，是否窄或宽，它包含的代码。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 MFC Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [在我的程序中启用 Unicode](../text/international-enabling.md)

- [在我的程序中启用 Unicode 和 MBCS](../text/internationalization-strategies.md)

- [使用 Unicode 创建国际化的程序](../text/unicode-programming-summary.md)

- [了解 Unicode 的优点](../text/benefits-of-character-set-portability.md)

- [使用 wmain 以便我可以将宽字符自变量传递到我的程序](../text/support-for-using-wmain.md)

- [请参阅 Unicode 编程摘要](../text/unicode-programming-summary.md)

- [了解字节宽度可移植性的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>请参阅
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)  
 [支持使用 wmain](../text/support-for-using-wmain.md)  