---
title: Unicode 和多字节字符集 (MBCS) 支持
ms.date: 1/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: 59e8759ffbe61b80c74d8b5aba5bc50886d6b23d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743913"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 和多字节字符集 (MBCS) 支持

某些语言，例如，日语和中文，有大型字符集。 若要支持这些市场编程，Microsoft 基础类库 (MFC) 使两个不同方法可以解决大型字符集：

- [Unicode](#mfc-support-for-unicode-strings)，`wchar_t`基于宽字符和字符串编码为 utf-16。

- [多字节字符集 (MBCS)](#mfc-support-for-mbcs-strings)， **char**基于单或双字节字符和特定于区域设置的字符集编码的字符串。

Microsoft 建议所有新开发的 MFC Unicode 库并在 Visual Studio 2013 和 Visual Studio 2015 中已弃用 MBCS 库。 这种情况不会再出现。 在 Visual Studio 2017 中删除了 MBCS 的弃用警告。

## <a name="mfc-support-for-unicode-strings"></a>MFC 对 Unicode 字符串的支持

为 Unicode 字符和字符串以宽字符存储为 UTF 16 有条件地启用整个 MFC 类库。 具体而言，类[CString](../atl-mfc-shared/reference/cstringt-class.md)完全支持 Unicode。

这些库，调试程序和 DLL 文件用于在 MFC 中支持 Unicode:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|MFC*version*U.LIB|MFC*version*U.PDB|MFC*version*U.DLL|MFC*version*UD.LIB|
|MFC*version*UD.PDB|MFC*version*UD.DLL|MFCS*version*U.LIB|MFCS*version*U.PDB|
|MFCS*version*UD.LIB|MFCS*version*UD.PDB|MFCM*version*U.LIB|MFCM*version*U.PDB|
|MFCM*version*U.DLL|MFCM*version*UD.LIB|MFCM*version*UD.PDB|MFCM*version*UD.DLL|

(*版本*表示版本号的文件; 例如，"140"意味着版本 14.0。)

`CString` 基于 TCHAR 数据类型。 如果生成的应用程序定义了符号 _UNICODE，则 TCHAR 被定义为类型`wchar_t`、 16 位字符编码类型。 否则，为定义 TCHAR **char**，正常的 8 位字符编码。 因此，在 Unicode，`CString`是 16 位字符组成。 而不是 Unicode，它构成类型的字符**char**。

应用程序的完整 Unicode 编程，则还必须：

- 使用 _T 宏有条件地代码文本字符串到可移植到 Unicode。

- 如果传递字符串，特别注意函数自变量需要以字符为单位的长度或以字节为单位的长度。 差异十分重要，如果您使用的 Unicode 字符串。

- 使用可移植版本的 C 运行时字符串处理函数。

- 使用以下数据类型的字符和字符指针：

   - 使用，会使用的 TCHAR **char**。

   - 使用，会使用的 LPTSTR **char**<strong>\*</strong>。

   - 使用，会使用的 LPCTSTR **const char**<strong>\*</strong>。 `CString` 提供了运算符 LPCTSTR 之间进行转换`CString`和 LPCTSTR。

`CString` 此外提供了识别 Unicode 的构造函数、 赋值运算符和比较运算符。

[运行时库参考](../c-runtime-library/c-run-time-library-reference.md)定义其所有字符串处理函数的可移植版本。 有关详细信息，请参阅类别[国际化](../c-runtime-library/internationalization.md)。

## <a name="mfc-support-for-mbcs-strings"></a>MFC 支持 MBCS 字符串

类库也已启用了多字节字符集，但仅为双字节字符设置 (DBCS)。

在多字节字符集的字符可以是一个或两个字节宽。 如果它是两个字节宽，其第一个字节是一个特殊"前导字节"，它是从特定范围，具体取决于哪些代码页正在使用中所选择的。 合起来看，前导字节和"尾字节"后，会指定在唯一的字符编码。

如果生成的应用程序定义了符号 _MBCS，键入 TCHAR，依据`CString`为基础，映射到**char**。 由您负责确定在哪些字节`CString`是前导字节，这是结尾字节。 C 运行时库提供帮助您确定这一点的函数。

在 DBCS 中，给定的字符串可以包含单字节的所有 ANSI 字符，所有双字节字符或两种方法的组合。 这些可能的操作需要谨慎处理在分析字符串。 这包括`CString`对象。

> [!NOTE]
> MFC 中的 Unicode 字符串序列化可以读取任何正在运行的应用程序的哪些版本的 Unicode 和 MBCS 字符串。 数据文件可以在 Unicode 和 MBCS 版本的应用程序之间移植。

`CString` 成员函数使用特殊的"通用文本"版本的 C 运行时函数调用它们，或它们使用识别 Unicode 的函数。 因此，例如，如果`CString`通常调用函数`strcmp`，它将调用相应的一般文本函数`_tcscmp`相反。 具体取决于如何定义的符号 _MBCS 和 _UNICODE，`_tcscmp`映射，如下所示：

|||
|-|-|
|已定义 _MBCS|`_mbscmp`|
|已定义 _UNICODE|`wcscmp`|
|两者都未定义|`strcmp`|

> [!NOTE]
> 符号 _MBCS 和 _UNICODE 是相互排斥的。

所有运行时字符串处理例程的一般文本函数映射中都讨论[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)。 有关列表，请参阅[国际化](../c-runtime-library/internationalization.md)。

同样，`CString`方法实现通过使用通用数据类型映射。 若要启用 MBCS 和 Unicode，MFC 使用的 TCHAR **char**或`wchar_t`，为 LPTSTR **char** <strong>\*</strong>或`wchar_t*`，和有关LPCTSTR**const char** <strong>\*</strong>或`const wchar_t*`。 这可确保正确的映射为 MBCS 或 Unicode。

## <a name="see-also"></a>请参阅

[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字符串操作](../c-runtime-library/string-manipulation-crt.md)
