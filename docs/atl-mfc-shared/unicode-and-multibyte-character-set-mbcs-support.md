---
title: Unicode 和多字节字符设置 (MBCS) 支持 |Microsoft 文档
ms.custom: ''
ms.date: 1/09/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8492e4a6777e4d609e3b457cfc77d1b8a691eed3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 和多字节字符集 (MBCS) 支持

某些语言中，例如，日语和中文，具有大型字符集。 为了支持这些市场编程，Microsoft 基础类库 (MFC)，请让两种不同方法来处理大型字符集：

- [Unicode](#mfc-support-for-unicode-strings)，`wchar_t`基于宽字符和字符串编码为 utf-16。

- [多字节字符集 (MBCS)](#mfc-support-for-mbcs-strings)，`char`基于单个或双字节字符和字符串中特定于区域设置的字符集编码。

Microsoft 建议所有新开发，MFC Unicode 库和 Visual Studio 2013 和 Visual Studio 2015 中已弃用 MBCS 库。 这种情况不会再出现。 已在 Visual Studio 2017 中删除了 MBCS 弃用警告。

## <a name="mfc-support-for-unicode-strings"></a>MFC 支持 Unicode 字符串

为 Unicode 字符和字符串存储在宽字符为 utf-16 有条件地启用整个 MFC 类库。 具体而言，类[CString](../atl-mfc-shared/reference/cstringt-class.md)完全支持 Unicode。

这些库、 调试器和 DLL 文件用于在 MFC 中支持 Unicode:

|||||
|-|-|-|-|
|UAFXCW。LIB|UAFXCW。PDB|UAFXCWD.LIB|UAFXCWD。PDB|
|MFC*版本*U.LIB|MFC*版本*U.PDB|MFC*版本*U.DLL|MFC*版本*UD。LIB|
|MFC*版本*UD。PDB|MFC*version*UD.DLL|MFCS*版本*U.LIB|MFCS*版本*U.PDB|
|MFCS*版本*UD。LIB|MFCS*版本*UD。PDB|MFCM*版本*U.LIB|MFCM*版本*U.PDB|
|MFCM*版本*U.DLL|MFCM*版本*UD。LIB|MFCM*版本*UD。PDB|MFCM*version*UD.DLL|

(*版本*表示的版本号的文件; 例如，"140"意味着版本 14.0。)

`CString` 基于`TCHAR`数据类型。 如果符号`_UNICODE`定义的程序，生成`TCHAR`被定义为类型`wchar_t`、 16 位字符编码类型。 否则为`TCHAR`定义为`char`，正常的 8 位字符编码。 因此，在 Unicode，`CString`是 16 位字符组成。 类型的字符组合而无需 Unicode， `char`。

到你的应用程序的完整 Unicode 编程，你还必须：

- 使用`_T`宏为有条件地代码文本字符串可移植到 Unicode。

- 当传递字符串时，注意到函数参数需要以字符为单位的长度或以字节为单位的长度。 区别便尤为重要，如果你使用的 Unicode 字符串。

- 使用可移植的 C 运行时字符串处理函数的版本。

- 用于字符和字符指针的以下数据类型：

   - 使用`TCHAR`在使用`char`。

   - 使用`LPTSTR`在使用`char*`。

   - 使用`LPCTSTR`在使用`const char*`。 `CString` 提供运算符`LPCTSTR`之间进行转换`CString`和`LPCTSTR`。

`CString` 此外提供 Unicode 意识的构造函数、 赋值运算符和比较运算符。

[运行时库参考](../c-runtime-library/c-run-time-library-reference.md)定义其所有字符串处理函数的可移植版本。 有关详细信息，请参阅类别[国际化](../c-runtime-library/internationalization.md)。

## <a name="mfc-support-for-mbcs-strings"></a>MFC 支持 MBCS 字符串

类库还启用了多字节字符集，但仅对双字节字符设置 (DBCS)。

集中的多字节字符的字符可以是一个或两个字节宽。 如果是双字节宽，其第一个字节是一个特殊"前导字节"，它是特定范围，具体取决于哪些代码页正在使用中的选择。 综上所述，前导字节和"尾字节"后，会指定在唯一字符编码。

如果符号`_MBCS`定义的程序类型生成`TCHAR`，在其上`CString`为基础，映射到`char`。 由您负责确定中的哪些字节`CString`是前导字节，哪些对象是结尾字节。 C 运行时库提供功能，以帮助你确定这一点。

在 DBCS 中，一个给定的字符串可包含所有单字节 ANSI 字符、 所有双字节字符或两个组合。 这些可能性在需要特别小心分析字符串。 这包括`CString`对象。

> [!NOTE]
> MFC 中的 Unicode 字符串序列化可以读取而不考虑的应用程序正在运行哪个版本的 Unicode 和 MBCS 字符串。 数据文件可以在 Unicode 和 MBCS 版本的程序之间移植。

`CString` 成员函数使用特殊的"通用文本"版本的 C 运行时函数调用它们，或它们使用 Unicode 意识的函数。 因此，例如，如果`CString`函数通常先调用`strcmp`，它会调用相应的一般文本函数`_tcscmp`相反。 具体取决于如何符号`_MBCS`和`_UNICODE`定义，`_tcscmp`映射，如下所示：

|||
|-|-|
|`_MBCS` 定义|`_mbscmp`|
|`_UNICODE` 定义|`wcscmp`|
|两者都未定义|`strcmp`|

> [!NOTE]
> 符号`_MBCS`和`_UNICODE`是互相排斥。

一般文本函数映射的所有运行时字符串处理例程中讨论了[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)。 有关列表，请参阅[国际化](../c-runtime-library/internationalization.md)。

同样，`CString`方法来实现通过使用通用数据类型映射。 若要启用 MBCS 和 Unicode，MFC 使用`TCHAR`为`char`或`wchar_t`，`LPTSTR`为`char*`或`wchar_t*`，和`LPCTSTR`为`const char*`或`const wchar_t*`。 这些都为 MBCS 或 Unicode 确保正确的映射。

## <a name="see-also"></a>请参阅

[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[字符串操作](../c-runtime-library/string-manipulation-crt.md)  
