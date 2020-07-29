---
title: Unicode 和多字节字符集 (MBCS) 支持
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: 217690e09ed595bb9fa9572693bf774259c42412
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219022"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 和多字节字符集 (MBCS) 支持

某些语言（如日语和中文）有大型字符集。 为了支持这些市场的编程，Microsoft 基础类库（MFC）支持两种不同的方法来处理大型字符集：

- [Unicode](#mfc-support-for-unicode-strings)基于 Unicode **`wchar_t`** 的宽字符和编码为 utf-16 的字符串。

- [多字节字符集（MBCS）](#mfc-support-for-mbcs-strings)， **`char`** 基于特定于区域设置的字符集中编码的单字节字符和字符串。

Microsoft 建议对所有新的开发使用 MFC Unicode 库，并且在 Visual Studio 2013 和 Visual Studio 2015 中弃用了 MBCS 库。 这种情况不会再出现。 Visual Studio 2017 中消除了 MBCS 弃用警告。

## <a name="mfc-support-for-unicode-strings"></a>MFC 对 Unicode 字符串的支持

对于以 utf-16 格式存储的 Unicode 字符和字符串，会有条件地启用整个 MFC 类库。 特别是，类[CString](../atl-mfc-shared/reference/cstringt-class.md)启用了 Unicode。

这些库、调试器和 DLL 文件用于支持 MFC 中的 Unicode：

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.板|UAFXCWD.LIB|UAFXCWD.板|
|MFC*版本*|MFC*版本*U .pdb|MFC*版本*U.DLL|MFC*版本*UD。LIB|
|MFC*版本*UD。板|MFC*版本*UD.DLL|MFCS*版本*|MFCS*版本*|
|MFCS*版本*UD。LIB|MFCS*版本*UD。板|MFCM*版本*|MFCM*版本*|
|MFCM*版本*U.DLL|MFCM*版本*UD。LIB|MFCM*版本*UD。板|MFCM*版本*UD.DLL|

（*版本*表示文件的版本号; 例如，"140" 表示版本14.0。）

`CString`基于 TCHAR 数据类型。 如果为程序的生成定义了符号 _UNICODE，则 TCHAR 将定义为类型，即 **`wchar_t`** 16 位字符编码类型。 否则，TCHAR 定义为 **`char`** 一般的8位字符编码。 因此，在 Unicode 下，包含 `CString` 16 位字符。 如果没有 Unicode，则由类型的字符组成 **`char`** 。

若要完成应用程序的 Unicode 编程，还必须执行以下操作：

- 使用 _T 宏按条件将文本字符串编码为可移植到 Unicode。

- 传递字符串时，请注意函数参数是否要求长度为个字符或长度（以字节为单位）。 如果使用 Unicode 字符串，则差异很重要。

- 使用 C 运行时字符串处理函数的可移植版本。

- 对于字符和字符指针，请使用下列数据类型：

  - 使用要使用的 TCHAR **`char`** 。

  - 使用要使用的 LPTSTR **`char`** <strong>\*</strong> 。

  - 使用 LPCTSTR，其中使用**const char** <strong>\*</strong> 。 `CString`提供要在和 LPCTSTR 之间进行转换的运算符 LPCTSTR `CString` 。

`CString`还提供了 Unicode 感知构造函数、赋值运算符和比较运算符。

[运行时库参考](../c-runtime-library/c-run-time-library-reference.md)定义其所有字符串处理函数的可移植版本。 有关详细信息，请参阅[国际化](../c-runtime-library/internationalization.md)。

## <a name="mfc-support-for-mbcs-strings"></a>用于 MBCS 字符串的 MFC 支持

类库对于多字节字符集也是启用的，但仅适用于双字节字符集（DBCS）。

在多字节字符集中，字符的宽度可以为1个或2个字节。 如果这两个字节宽，则其第一个字节是从特定范围中选择的特殊 "前导字节"，具体取决于所使用的代码页。 一起使用时，"前导字节" 指定唯一的字符编码。

如果为程序的生成定义了符号 _MBCS，则键入 TCHAR （ `CString` 基于）将映射到 **`char`** 。 确定中的哪些字节 `CString` 是前导字节，哪些是尾字节。 C 运行时库提供可帮助您确定这一点的函数。

在 DBCS 下，给定字符串可以包含所有单字节 ANSI 字符、所有双字节字符或二者的组合。 这些可能需要特别注意分析字符串。 这包括 `CString` 对象。

> [!NOTE]
> MFC 中的 unicode 字符串序列化可读取 Unicode 和 MBCS 字符串，无论正在运行的应用程序的版本是什么。 你的数据文件可在程序的 Unicode 和 MBCS 版本之间移植。

`CString`成员函数使用它们调用的 C 运行时函数的特殊 "通用文本" 版本，或使用 Unicode 感知函数。 例如，如果一个 `CString` 函数通常调用 `strcmp` ，则它会调用相应的一般文本函数 `_tcscmp` 。 根据定义符号 _MBCS 和 _UNICODE 的方式，将 `_tcscmp` 映射如下：

|||
|-|-|
|已定义 _MBCS|`_mbscmp`|
|已定义 _UNICODE|`wcscmp`|
|未定义符号|`strcmp`|

> [!NOTE]
> _MBCS 和 _UNICODE 符号互相排斥。

[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)中讨论了所有运行时字符串处理例程的一般文本函数映射。 有关列表，请参阅[国际化](../c-runtime-library/internationalization.md)。

同样， `CString` 方法是使用泛型数据类型映射实现的。 为了同时启用 MBCS 和 Unicode，MFC 将 TCHAR 用于 **`char`** 或 **`wchar_t`** ，LPTSTR 用于 **`char`** <strong>\*</strong> 或 `wchar_t*` ，并 LPCTSTR 用于**const char** <strong>\*</strong> 或 `const wchar_t*` 。 这可以确保 MBCS 或 Unicode 的正确映射。

## <a name="see-also"></a>另请参阅

[字符串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字符串操作](../c-runtime-library/string-manipulation-crt.md)
