---
title: 字符串数据管理
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317455"
---
# <a name="string-data-management"></a>字符串数据管理

可视化C++提供了几种管理字符串数据的方法：

- 用于使用 C 样式空终止字符串的[字符串操作](../c-runtime-library/string-manipulation-crt.md)

- 用于管理字符串的 Win32 API 函数

- MFC 的类[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)， 提供灵活、可调整大小的字符串对象

- 类[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)， 它提供与 MFC 无关的字符串对象，其功能与`CString`

几乎所有程序都使用字符串数据。 MFC 的`CString`类通常是灵活字符串处理的最佳解决方案。 从版本 7.0`CString`开始，可用于 MFC 或与 MFC 无关的程序。 运行时库和支持`CString`字符串都包含多字节（宽）字符，如 Unicode 或 MBCS 编程中。

本文介绍了类库提供的与字符串操作相关的通用服务。 本文涵盖的主题包括：

- [Unicode 和 MBCS 提供可移植性](#_core_unicode_and_mbcs_provide_portability)

- [CStrings 和 const 字符指针](#_core_cstrings_and_const_char_pointers)

- [CString 引用计数](#_core_cstring_reference_counting)

[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)支持操作字符串。 它旨在替换和扩展 C 运行时库字符串包通常提供的功能。 类`CString`提供成员函数和运算符，以便简化字符串处理，类似于 Basic 中的函数和运算符。 该类还提供构造函数和运算符，用于构造、分配和比较`CString`和标准C++字符串数据类型。 因为`CString`不是派生自`CObject`，因此可以使用独立于`CString`大多数 Microsoft 基础类库 （MFC） 的对象。

`CString`对象遵循"值语义"。 对象`CString`表示唯一值。 将 一`CString`个视为实际字符串，而不是指向字符串的指针。

对象`CString`表示可变字符数的序列。 `CString`对象可以被视为字符数组。

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode 和 MBCS 提供可移植性

使用 MFC 版本 3.0 及更高版本`CString`时，MFC（包括 ）同时为 Unicode 和多字节字符集 （MBCS） 启用。 通过这种支持，您可以更轻松地编写可为 Unicode 或 ANSI 字符构建的可移植应用程序。 要启用此可移植性，`CString`对象中的每个字符都为 TCHAR 类型，该字符的定义`wchar_t`是，在生成应用程序时定义符号_UNICODE，或者定义`char`符号。" 字符`wchar_t`宽 16 位。 如果使用定义的符号_MBCS生成，则启用 MBCS。 MFC 本身使用定义的_MBCS符号（用于 NAFX 库）或_UNICODE符号（对于 UAFX 库）构建。

> [!NOTE]
> 本`CString`中的示例和字符串上附带的文章显示了为 Unicode 可移植性正确格式化的文本字符串，使用_T宏，该宏将文本字符串转换为窗体：

`L"literal string"`

> [!NOTE]
> 编译器将其视为 Unicode 字符串。 例如，以下代码：

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> 如果定义_UNICODE或 ANSI 字符串（如果不是）则转换为 Unicode 字符串。 有关详细信息，请参阅文章[Unicode 和多字节字符集 （MBCS） 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

对象`CString`最多可以存储INT_MAX （2，147，483，647） 个字符。 TCHAR 数据类型用于获取或设置`CString`对象内的单个字符。 与字符数组不同，`CString`类具有内置内存分配功能。 这允许`CString`对象根据需要自动增长（也就是说，您不必担心将`CString`对象增长到适合较长的字符串）。

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings 和 const 字符指针

对象`CString`也可以像文本 C 样式字符串（如果`PCXSTR`不在 Unicode 下，它与**const char**<strong>\*</strong>相同）。 [CSimpleStringT：：运算符 PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)转换运算符`CString`允许对象在函数调用中自由替换字符指针。 **CString（ LPCWSTR** `pszSrc` **）** 构造函数允许用字符指针替换`CString`对象。

未尝试折叠`CString`对象。 如果使两`CString`个对象包含`Chicago`，例如， 中的`Chicago`字符存储在两个位置。 （MFC 的未来版本可能并非如此，因此不应依赖它。

> [!NOTE]
> 当您需要直接访问 作为`CString`指向字符的非常量指针时，请使用[CSimpleStringT：getBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT：：释放缓冲区](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成员函数。

> [!NOTE]
> 使用[CStringT：AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)和[CStringT：SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成员函数来分配和设置自动化中使用的 BSTR 对象（以前称为 OLE 自动化）。

> [!NOTE]
> 在可能的情况下，在帧`CString`上而不是在堆上分配对象。 这样可以节省内存并简化参数传递。

类`CString`不作为 Microsoft 基础类库集合类实现，但`CString`对象当然可以作为集合中的元素存储。

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString 引用计数

从 MFC 版本 4.0 开始，复制[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)对象时，MFC 将递增引用计数，而不是复制数据。 这使得按值传递参数和按值返回`CString`对象的效率更高。 这些操作会导致调用复制构造函数，有时不止一次调用。 增加引用计数可减少这些常见操作的开销，并使使用`CString`选项更具吸引力。

销毁每个副本时，原始对象的引用计数将递减。 原始`CString`对象不会销毁，直到其引用计数减少到零。

您可以使用`CString`成员函数[CSimpleStringT：：锁定缓冲区](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[CSimpleStringT：解锁缓冲区](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)来禁用或启用引用计数。

## <a name="see-also"></a>另请参阅

[一般 MFC 主题](../mfc/general-mfc-topics.md)
