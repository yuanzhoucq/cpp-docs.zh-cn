---
title: 字符串数据管理
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 2da8967effeb6ff439cf5b3cece31f63ee77a761
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219035"
---
# <a name="string-data-management"></a>字符串数据管理

Visual C++ 提供多种方法来管理字符串数据：

- 用于处理以 null 结尾的 C 样式字符串的[字符串操作](../c-runtime-library/string-manipulation-crt.md)

- 用于管理字符串的 Win32 API 函数

- MFC 的类[CStringT 类，该类](../atl-mfc-shared/reference/cstringt-class.md)提供灵活、可调整大小的字符串对象

- 类[CStringT 类，该类](../atl-mfc-shared/reference/cstringt-class.md)提供与 MFC 无关的字符串对象，其功能与`CString`

几乎所有程序都适用于字符串数据。 MFC 的 `CString` 类通常是用于灵活的字符串处理的最佳解决方案。 从版本7.0 开始， `CString` 可以在 mfc 或与 mfc 无关的程序中使用。 运行时库和 `CString` 支持包含多字节（宽）字符的字符串，如 Unicode 或 MBCS 编程中所示。

本文介绍类库提供的与字符串操作相关的通用服务。 本文中涵盖的主题包括：

- [Unicode 和 MBCS 提供可移植性](#_core_unicode_and_mbcs_provide_portability)

- [CStrings 和 const char 指针](#_core_cstrings_and_const_char_pointers)

- [CString 引用计数](#_core_cstring_reference_counting)

[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)提供对操作字符串的支持。 它旨在替换和扩展由 C 运行时库字符串包正常提供的功能。 `CString`类提供用于简化字符串处理的成员函数和运算符，类似于基本的。 类还提供构造函数和运算符，用于构造、分配和比较 `CString` s 和标准 c + + 字符串数据类型。 由于不 `CString` 是派生自 `CObject` ，因此可以使用 `CString` 独立于大多数 Microsoft 基础类库（MFC）的对象。

`CString`对象遵循 "值语义"。 `CString`对象表示一个唯一值。 将 `CString` 作为实际的字符串，而不是指向字符串的指针。

`CString`对象表示可变数量的字符的序列。 `CString`对象可以被视为字符数组。

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode 和 MBCS 提供可移植性

对于 MFC 版本3.0 及更高版本， `CString` 将为 Unicode 和多字节字符集（MBCS）启用 mfc，包括。 这种支持使你可以更轻松地编写可为 Unicode 或 ANSI 字符生成的可移植应用程序。 若要启用此可移植性，对象中的每个字符 `CString` 都是 TCHAR 类型，其定义方式如下：在 **`wchar_t`** 生成应用程序时定义符号 _UNICODE; 否则为 **`char`** 。 **`wchar_t`** 字符的宽度为16位。 如果生成时 _MBCS 定义了符号，则将启用 MBCS。 MFC 本身是用 _MBCS 符号（适用于 NAFX 库）或所定义的 _UNICODE 符号（适用于 UAFX 库）生成的。

> [!NOTE]
> `CString`这篇文章中的示例以及附带的有关字符串的文章显示了使用 _T 宏正确设置了 Unicode 可移植性的字符串格式，这会将文本字符串转换为以下形式：

`L"literal string"`

> [!NOTE]
> 编译器将其视为 Unicode 字符串。 例如，以下代码：

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> 如果 _UNICODE 定义或为 ANSI 字符串，则转换为 Unicode 字符串（如果不是）。 有关详细信息，请参阅文章[Unicode 和多字节字符集（MBCS）支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

`CString`对象最多可存储 INT_MAX （2147483647）个字符。 TCHAR 数据类型用于获取或设置对象内的单个字符 `CString` 。 不同于字符数组， `CString` 类具有内置的内存分配功能。 这允许 `CString` 对象根据需要自动增长（也就是说，无需担心增大 `CString` 对象以适应更长的字符串）。

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings 和 const char 指针

`CString`对象也可以像文本 C 样式字符串（ `PCXSTR` 如果不在 Unicode 下，则与**const char**相同 <strong>\*</strong> ）。 [CSimpleStringT：： OPERATOR PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)转换运算符允许 `CString` 对象在函数调用中自由替换为字符指针。 **CString （LPCWSTR** `pszSrc` **）** 构造函数允许将字符指针替换为 `CString` 对象。

不尝试折叠 `CString` 对象。 例如，如果您创建了两个 `CString` 对象 `Chicago` （例如），则中的字符 `Chicago` 存储在两个位置。 （这对于 MFC 的未来版本可能不是如此，因此你不应依赖于它。）

> [!NOTE]
> 当需要直接访问作为指向字符的非常量指针时，请使用[CSimpleStringT：： GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT：： ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成员函数 `CString` 。

> [!NOTE]
> 使用[CStringT：： AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)和[CStringT：： SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成员函数可以分配和设置在自动化中使用的 BSTR 对象（以前称为 OLE 自动化）。

> [!NOTE]
> 如果可能，请在 `CString` 帧上分配对象，而不是在堆上分配。 这会节省内存并简化参数传递。

`CString`类未实现为 Microsoft 基础类库集合类，但 `CString` 对象当然可以存储为集合中的元素。

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString 引用计数

在 MFC 版本4.0 中，复制[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)对象时，MFC 会递增引用计数，而不是复制数据。 这会按值传递参数，并 `CString` 以更高效的值返回对象。 这些操作将导致调用复制构造函数，有时会出现多次。 递增引用计数可减少这些常见操作的开销，并使用 `CString` 更具吸引力的选项。

销毁每个副本时，原始对象中的引用计数将减少。 原始 `CString` 对象在其引用计数缩减为零时才会被销毁。

您可以使用 `CString` 成员函数[CSimpleStringT：： LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[CSimpleStringT：： UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)来禁用或启用引用计数。

## <a name="see-also"></a>另请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)
