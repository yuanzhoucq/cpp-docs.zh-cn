---
title: 字符串数据管理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6b54bfbf614ca7e3d1c34c4924c545c5f46ed4e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763716"
---
# <a name="string-data-management"></a>字符串数据管理

Visual c + + 提供多种方式来管理字符串数据：

- [字符串操作](../c-runtime-library/string-manipulation-crt.md)使用以 null 结尾的 C 样式字符串

- 用于管理字符串的 Win32 API 函数

- MFC 的类[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)，提供灵活、 可调整大小的字符串对象

- 类[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)，其中具有相同的功能提供一个独立于 MFC 的字符串对象 `CString`

几乎所有程序都都使用字符串数据。 MFC 的`CString`类通常是灵活的字符串处理的最佳解决方案。 从版本 7.0，开始`CString`可以在 MFC 或 MFC 独立于程序中使用。 这两个运行时库和`CString`支持包含多字节 （宽） 字符，如 Unicode 或 MBCS 编程中所示的字符串。

本指南介绍了类库提供了有关字符串操作的通用服务。 在本文中涵盖的主题包括：

- [Unicode 和 MBCS 提供可移植性](#_core_unicode_and_mbcs_provide_portability)

- [Cstring 和 const char 指针](#_core_cstrings_and_const_char_pointers)

- [CString 引用计数](#_core_cstring_reference_counting)

[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)类提供用于操作字符串的支持。 它旨在替换和扩展通常由 C 运行时库字符串包提供的功能。 `CString`类提供成员函数和运算符的简化的字符串处理，类似于在 Basic 中的那些。 该类还提供构造函数和运算符的构造、 分配和比较`CString`s 和标准 c + + 字符串数据类型。 因为`CString`不派生自`CObject`，可以使用`CString`独立于大多数的 Microsoft 基础类库 (MFC) 的对象。

`CString` 对象遵循"值语义。" 一个`CString`对象表示一个唯一值。 想一想`CString`作为实际的字符串，而不是指向字符串的指针。

一个`CString`对象表示的可变数量的字符序列。 `CString` 可以将对象视为字符数组。

##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode 和 MBCS 提供可移植性

MFC 3.0 版及更高版本，MFC，其中包括`CString`，启用了对 Unicode 和多字节字符集 (MBCS)。 此支持，使你更轻松地编写可移植应用程序可以生成用于 Unicode 或 ANSI 字符。 若要启用此可移植性，在每个字符`CString`对象属于类型 TCHAR，tchar 指`wchar_t`如果定义了符号 _UNICODE 时生成应用程序，或作为`char`如果不是。 一个`wchar_t`字符为 16 位宽。 如果您使用符号已定义 _MBCS 生成，启用 MBCS。 使用 （适用于 NAFX 库中） 的 _MBCS 符号生成 MFC 本身或定义了 _UNICODE 符号 （适用于 UAFX 库中）。

> [!NOTE]
>  `CString`这和字符串的随附文章中的示例显示 Unicode 可移植性，使用 _T 宏，将向窗体的文本字符串转换为正确设置格式的文本字符串：

`L"literal string"`

> [!NOTE]
>  该编译器将为 Unicode 字符串。 例如，以下代码：

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
>  将转换为 Unicode 字符串，如果定义了 _UNICODE 或如果不是 ANSI 字符串。 有关详细信息，请参阅文章[Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

一个`CString`对象可以存储为 INT_MAX (2147483647) 个字符。 TCHAR 数据类型用于获取或设置内的单个字符`CString`对象。 与字符数组不同`CString`类具有内置的内存分配功能。 这允许`CString`对象以根据需要自动增加 (即，不需要担心如何增长`CString`对象以适应较长的字符串)。

##  <a name="_core_cstrings_and_const_char_pointers"></a> Cstring 和 const char 指针

一个`CString`对象也可以充当 C 样式字符串 ( `PCXSTR`，这是与相同**const char** <strong>\*</strong>如果不在 Unicode)。 [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)转换运算符允许`CString`对象自由地替换为函数调用中的字符指针。 **CString (LPCWSTR** `pszSrc` **)** 构造函数允许字符指针来替换的`CString`对象。

未尝试折叠`CString`对象。 如果使两个`CString`对象包含`Chicago`，例如，在字符`Chicago`存储在两个位置中。 （这可能不为 true 的未来版本的 MFC，因此不应依赖于它。）

> [!NOTE]
>  使用[CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)并[CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成员函数时您需要直接访问`CString`作为指向字符的非常量指针。

> [!NOTE]
>  使用[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)并[CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成员函数来分配和设置自动化 （以前称为 OLE 自动化） 中所用的 BSTR 对象。

> [!NOTE]
>  在可能的情况下，分配`CString`帧，而不是在堆上的对象。 这会保存内存并简化了参数传递。

`CString`类未实现作为 Microsoft 基础类库集合类，但是`CString`对象肯定可以存储为集合中的元素。

##  <a name="_core_cstring_reference_counting"></a> CString 引用计数

从 MFC 版本 4.0 中，开始时[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)对象复制、 MFC 递增引用计数，而不是将数据复制。 这样，将参数传递的值并返回`CString`通过更有效的值的对象。 这些操作会导致复制构造函数调用，有时需要超过一次。 递增引用计数减少了这些常见操作的开销，并使使用`CString`更具吸引力的选项。

因为每个副本将被销毁，原始对象中的引用计数将减少。 原始`CString`直到其引用计数减少到零时，对象不会被销毁。

可以使用`CString`成员函数[CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)并[CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)禁用或启用引用计数。

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)

