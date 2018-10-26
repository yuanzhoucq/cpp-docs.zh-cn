---
title: Unicode 编程摘要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ac931aca05c9df6d5b201fdafb8872c1ee9c789
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080671"
---
# <a name="unicode-programming-summary"></a>Unicode 编程摘要

若要充分利用 Unicode 的 MFC 和 C 运行时支持，需要：

- 定义`_UNICODE`。

   定义符号`_UNICODE`构建您的程序之前。

- 指定入口点。

   上**输出**页**链接器**中项目的文件夹[属性页](../ide/property-pages-visual-cpp.md)对话框中，将**入口点**为符号`wWinMainCRTStartup`.

- 使用可移植运行时函数和类型。

   使用适当的 C 运行时函数的 Unicode 字符串处理。 可以使用`wcs`系列函数，但你可能倾向于 （国际上已启用） 完全可移植`_TCHAR`宏。 这些宏都带有前缀`_tcs`; 来替代，一个用于其中一个，为`str`函数系列。 这些函数有详细介绍[国际化](../c-runtime-library/internationalization.md)一部分*运行时库参考*。 有关详细信息，请参阅[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。

   使用`_TCHAR`和相关的可移植数据类型中所述[适用于 Unicode 支持](../text/support-for-unicode.md)。

- 正确地处理字符串。

   Visual c + + 编译器将解释为文本字符串编码为：

    ```cpp
    L"this is a literal string"
    ```

   表示 Unicode 字符的字符串。 为原义字符，可以使用相同的前缀。 使用`_T`一般情况下，代码文本字符串，使它们编译为 Unicode 字符串下 Unicode 或 ANSI 字符串 （包括 MBCS） 而无需 Unicode 宏。 例如，而不是:

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   使用：

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   与`_UNICODE`定义，`_T`转换的文字字符串 L 前缀的格式。 否则为`_T`转换不带 L 前缀的字符串。

    > [!TIP]
    >  `_T`宏等同于`_TEXT`宏。

- 请注意传递到函数的字符串长度。

   某些函数需要一个字符串; 中的字符数其他人想要字节的数。 例如，如果`_UNICODE`定义，则以下调用`CArchive`不起作用对象 (`str`是`CString`):

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   在 Unicode 应用程序中，长度可以字符数，但未正确字节数，因为每个字符宽的 2 个字节。 相反，您必须使用：

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   它指定正确的要写入字节数。

   但是，MFC 成员是面向字符的而不是面向字节的工作函数无需此额外的编码：

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` 采用字符，不是数字的字节的数。

- 使用[fopen_s、 _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)打开 Unicode 文件。

总之，MFC 和运行时库提供以下支持的 Unicode 编程：

- 除了数据库类成员函数，所有 MFC 函数都都支持 Unicode，包括`CString`。 `CString` 此外提供了 Unicode/ANSI 转换函数。

- 运行时库提供的所有字符串处理函数的 Unicode 版本。 （在运行时库还提供了合适的可移植版本为 Unicode 或 MBCS。 这些是`_tcs`宏。)

- Tchar.h 提供可移植的数据类型和`_T`宏用于转换文本字符串和字符。 有关详细信息，请参阅[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。

- 在运行时库提供的宽字符版本`main`。 使用`wmain`使能够识别 Unicode 应用程序。

## <a name="see-also"></a>请参阅

[支持 Unicode](../text/support-for-unicode.md)