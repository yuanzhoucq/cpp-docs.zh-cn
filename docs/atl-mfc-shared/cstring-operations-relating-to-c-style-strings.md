---
title: 与 C 样式字符串相关的 CString 操作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 765cb6ccf24415c174761c57268dc79e1fc6845b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062556"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>与 C 样式字符串相关的 CString 操作

一个[CString](../atl-mfc-shared/using-cstring.md)对象包含字符串数据。 `CString` 继承的一套[方法和运算符](../atl-mfc-shared/reference/cstringt-class.md)类模板中定义的[CStringT](../atl-mfc-shared/reference/cstringt-class.md)用于处理字符串数据。 (`CString`是**typedef**的专门`CStringT`若要使用的字符数据类型的`CString`支持。)

`CString` 不会将字符数据内部存储为 C 样式 null 结尾的字符串。 相反，`CString` 会跟踪字符数据的长度，以便可以更安全地观察其所需的数据和空间。

`CString` 接受 C 样式字符串，并且提供作为 C 样式字符串访问字符数据的方式。 本主题包含以下部分，说明如何将 `CString` 对象当作 C 样式 null 结尾的字符串来使用。

- [将转换为 C 样式 null 结尾的字符串](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [使用标准运行时库字符串函数](#_core_working_with_standard_run.2d.time_library_string_functions)

- [直接修改 CString 内容](#_core_modifying_cstring_contents_directly)

- [将 CString 对象与可变自变量函数一起使用](#_core_using_cstring_objects_with_variable_argument_functions)

- [指定 CString 形参](#_core_specifying_cstring_formal_parameters)

##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> 将 CString 用作 C 样式 Null 结尾的字符串

若要使用`CString`对象作为 C 样式字符串，请将对象转换为 LPCTSTR。 在以下示例中，`CString` 将返回指向只读 C 样式 null 结尾的字符串的指针。 `strcpy` 函数将 C 样式字符串的副本放入变量 `myString` 中。

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

你可以使用 `CString` 方法（例如 `SetAt`）来修改字符串对象中的单个字符。 但是，LPCTSTR 指针是临时的并且对进行任何更改时变为无效`CString`。 `CString` 还可能超出范围，并且被自动删除。 我们建议您让的全新 LPCTSTR 指针`CString`对象每次使用一个。

有时你可能需要 `CString` 数据的副本以直接修改。 使用更安全的函数 `strcpy_s`（或者 Unicode/MBCS 可移植 `_tcscpy_s`）将 `CString` 对象复制到单独的缓冲区中。 这是可安全修改字符的位置，如以下示例所示。

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> 第三个参数`strcpy_s`(或 Unicode/MBCS 可移植`_tcscpy_s`) 是`const wchar_t*`(Unicode) 或`const char*`(ANSI)。 上面的示例为此自变量传递 `CString`。 C++ 编译器自动应用针对 `CString` 类定义的转换函数，此函数可将 `CString` 转换为 `LPCTSTR`。 定义从一种类型到另一种类型的强制转换操作的功能是 C++ 的最有用的功能之一。

##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> 使用标准运行时库字符串函数

你应该可以找到一个 `CString` 方法以执行任何字符串操作，对于此操作，你可以考虑使用标准 C 运行时库字符串函数，例如 `strcmp`（或 Unicode/MBCS 可移植 `_tcscmp`）。

如果必须使用 C 运行时字符串函数，可以使用 _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string 中所述的技术。 你可以将 `CString` 对象复制到等效的 C 样式字符串缓冲区，在该缓冲区上执行你的操作，然后将结果 C 样式字符串分配回 `CString` 对象。

##  <a name="_core_modifying_cstring_contents_directly"></a> 直接修改 CString 内容

在大部分情况下，你应该使用 `CString` 成员函数修改 `CString` 对象的内容或将 `CString` 转换为 C 样式字符串。

某些情况下，直接修改 `CString` 内容很有意义，例如，在你使用需要字符缓冲区的操作系统函数时。

`GetBuffer` 和 `ReleaseBuffer` 方法提供对 `CString` 对象的内部字符缓冲区的访问权限，并使你可以直接修改它。 以下步骤介绍如何将这些函数用于此目的。

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>使用 GetBuffer 和 ReleaseBuffer 访问 CString 对象的内部字符缓冲区

1. 为 `GetBuffer` 对象调用 `CString` 并指定所需的缓冲区的长度。

1. 使用由 `GetBuffer` 返回的指针以将字符直接写入 `CString` 对象中。

1. 为 `ReleaseBuffer` 对象调用 `CString` 以更新所有内部 `CString` 状态信息，例如，字符串的长度。 直接修改 `CString` 对象的内容后，你必须在调用任何其他 `ReleaseBuffer` 成员函数前先调用 `CString`。

##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> 将 CString 对象使用与可变自变量函数

某些 C 函数采用数量可变的自变量。 一个要注意的示例是 `printf_s`。 由于声明这种函数的方法，编译器无法确定参数的类型，并且无法确定每个参数上要执行何种转换操作。 因此，在将 `CString` 对象传递到采用数量可变的自变量的函数时，使用显示类型强制转换非常重要。

若要使用`CString`中的变量自变量函数，显式转换对象`CString`为 LPCTSTR 字符串，如下面的示例中所示。

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

##  <a name="_core_specifying_cstring_formal_parameters"></a> 指定 CString 形参

对于需要字符串自变量的大部分函数，最好将函数原型中的形参指定为指向某个字符 (`const`) 的 `LPCTSTR` 指针，而不是 `CString`。 当将形参指定为`const`指向字符的指针，你可以向 TCHAR 数组，文本字符串中传递一个指针，或者 [`"hi there"`]，或`CString`对象。 `CString`对象将自动转换为 LPCTSTR。 可以使用 LPCTSTR 的任何位置，也可以使用`CString`对象。

您可以将形参指定为常量字符串引用 (即， `const CString&`) 如果该参数不会被修改。 Drop **const**修饰符，如果该函数将修改该字符串。 如果需要默认的 null 值，则将其初始化为 null 字符串 [`""`]，如下所示：

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

对于大部分函数结果，你可以轻松地通过值返回 `CString` 对象。

## <a name="see-also"></a>请参阅

[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString 参数传递](../atl-mfc-shared/cstring-argument-passing.md)
