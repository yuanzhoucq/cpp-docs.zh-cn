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
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317441"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 和多字节字符集 (MBCS) 支持

某些语言（例如日语和中文）具有较大的字符集。 为了支持这些市场的编程，Microsoft 基础类库 （MFC） 支持两种不同的方法来处理大型字符集：

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` ， 基于宽字符和字符串编码为 UTF-16.

- [多字节字符集 （MBCS），](#mfc-support-for-mbcs-strings)基于**字符**的单字节或双字节字符和字符串编码在区域设置特定的字符集中.

Microsoft 已为所有新开发推荐 MFC Unicode 库，在 Visual Studio 2013 和 Visual Studio 2015 中弃用 MBCS 库。 这种情况不会再出现。 在 Visual Studio 2017 中删除了 MBCS 弃用警告。

## <a name="mfc-support-for-unicode-strings"></a>MFC 支持 Unicode 字符串

整个 MFC 类库有条件地启用 Unicode 字符和字符串，这些字符和字符串以宽字符存储为 UTF-16。 特别是，类[CString](../atl-mfc-shared/reference/cstringt-class.md)启用了 Unicode。

这些库、调试器和 DLL 文件用于支持 MFC 中的 Unicode：

|||||
|-|-|-|-|
|UAFXCW.自由|UAFXCW.Pdb|UAFXCWD.自由|UAFXCWD.Pdb|
|MFC*版本*U.LIB|MFC*版本*U.PDB|MFC*版本*U.DLL|MFC*版本*UD。自由|
|MFC*版本*UD。Pdb|MFC*版本*UD。Dll|MFCS*版本*U.LIB|MFCS*版本*U.PDB|
|MFCS*版本*UD。自由|MFCS*版本*UD。Pdb|MFCM*版本*U.LIB|MFCM*版本*U.PDB|
|MFCM*版本*U.DLL|MFCM*版本*UD。自由|MFCM*版本*UD。Pdb|MFCM*版本*UD。Dll|

（*版本*表示文件的版本号;例如，"140"表示版本 14.0。

`CString`基于 TCHAR 数据类型。 如果为程序的生成定义了符号_UNICODE，则 TCHAR 定义为类型`wchar_t`，即 16 位字符编码类型。 否则，TCHAR 被定义为**字符**，即正常的 8 位字符编码。 因此，在 Unicode`CString`下， a 由 16 位字符组成。 没有 Unicode，它由**字符**类型的字符组成。

要完成应用程序的 Unicode 编程，还必须：

- 使用_T宏有条件地将文本字符串编码为可移植到 Unicode。

- 传递字符串时，请注意函数参数是需要以字符为单位的长度还是以字节为单位的长度。 如果使用 Unicode 字符串，则差异很重要。

- 使用 C 运行时字符串处理函数的可移植版本。

- 对字符和字符指针使用以下数据类型：

  - 使用 TCHAR，您将使用**字符**。

  - 使用 LPTSTR，您将在其中使用**字符**<strong>\*</strong>。

  - 使用 LPCTSTR，您将在其中使用**const char**<strong>\*</strong>。 `CString`提供运算符 LPCTSTR 在`CString`和 LPCTSTR 之间转换。

`CString`还提供 Unicode 感知构造函数、赋值运算符和比较运算符。

[运行时库参考](../c-runtime-library/c-run-time-library-reference.md)定义其所有字符串处理功能的可移植版本。 有关详细信息，请参阅类别["国际化](../c-runtime-library/internationalization.md)"。

## <a name="mfc-support-for-mbcs-strings"></a>MFC 支持 MBCS 字符串

类库还启用多字节字符集，但仅适用于双字节字符集 （DBCS）。

在多字节字符集中，字符可以是一个或两个字节宽。 如果它是两个字节宽，则其第一个字节是从特定范围内选择的特殊"潜在顾客字节"，具体取决于正在使用的代码页。 综合起来，潜在顾客和"跟踪字节"指定唯一的字符编码。

如果为程序的生成定义了符号_MBCS，则键入基于 TCHAR 的"TCHAR"，`CString`将映射到**char**。 由您确定中的`CString`哪个字节是潜在顾客字节，哪些字节是跟踪字节。 C 运行时库提供函数，以帮助您确定这一点。

在 DBCS 下，给定字符串可以包含所有单字节 ANSI 字符、所有双字节字符或两者的组合。 这些可能性需要特别小心解析字符串。 这包括`CString`对象。

> [!NOTE]
> MFC 中的 Unicode 字符串序列化可以读取 Unicode 和 MBCS 字符串，而不管正在运行的应用程序的版本如何。 您的数据文件在程序的 Unicode 和 MBCS 版本之间是可移植的。

`CString`成员函数使用它们调用的 C 运行时函数的特殊"泛文本"版本，或者它们使用 Unicode 感知函数。 因此，例如，如果函数`CString`通常调用`strcmp`，则改为调用相应的泛文本函数。 `_tcscmp` 根据符号_MBCS和_UNICODE的定义方式，`_tcscmp`地图如下：

|||
|-|-|
|已定义 _MBCS|`_mbscmp`|
|已定义 _UNICODE|`wcscmp`|
|两个符号均未定义|`strcmp`|

> [!NOTE]
> _MBCS和_UNICODE的符号是相互排斥的。

[C 运行时库引用](../c-runtime-library/c-run-time-library-reference.md)中讨论了所有运行时字符串处理例程的泛文本函数映射。 有关列表，请参阅[国际化](../c-runtime-library/internationalization.md)。

同样，`CString`通过使用泛型数据类型映射实现方法。 要同时启用 MBCS 和 Unicode，MFC 使用`wchar_t`**TCHAR**用于字符或`wchar_t*`，LPTSTR 表示**字符**<strong>\*</strong>或 ，LPCTSTR 用于**const char**<strong>\*</strong>或`const wchar_t*`。 这些可确保 MBCS 或 Unicode 的正确映射。

## <a name="see-also"></a>另请参阅

[字符串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字符串操作](../c-runtime-library/string-manipulation-crt.md)
