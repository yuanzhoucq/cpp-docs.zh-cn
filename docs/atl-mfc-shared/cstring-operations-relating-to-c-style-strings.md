---
title: 与 C 样式字符串相关的 CString 操作
ms.date: 11/04/2016
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
ms.openlocfilehash: 406a934d3691c7787085cc319770074ac2ee5926
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317947"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>与 C 样式字符串相关的 CString 操作

[CString](../atl-mfc-shared/using-cstring.md)对象包含字符串数据。 `CString`继承类模板[CStringT](../atl-mfc-shared/reference/cstringt-class.md)中定义的[方法和运算符](../atl-mfc-shared/reference/cstringt-class.md)的集，以便处理字符串数据。 （`CString`是专门用于处理`CString`支持的字符`CStringT`数据类型的类型**定义**。

`CString` 不会将字符数据内部存储为 C 样式 null 结尾的字符串。 相反，`CString` 会跟踪字符数据的长度，以便可以更安全地观察其所需的数据和空间。

`CString` 接受 C 样式字符串，并且提供作为 C 样式字符串访问字符数据的方式。 本主题包含以下部分，说明如何将 `CString` 对象当作 C 样式 null 结尾的字符串来使用。

- [转换为 C 样式 null 结尾的字符串](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [使用标准运行时库字符串函数](#_core_working_with_standard_run.2d.time_library_string_functions)

- [直接修改 CString 内容](#_core_modifying_cstring_contents_directly)

- [使用具有变量参数函数的 CString 对象](#_core_using_cstring_objects_with_variable_argument_functions)

- [指定 CString 正式参数](#_core_specifying_cstring_formal_parameters)

## <a name="using-cstring-as-a-c-style-null-terminated-string"></a><a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a>使用 CString 作为 C 样式空终止字符串

要将`CString`对象用作 C 样式字符串，将对象强制转换为 LPCTSTR。 在以下示例中，`CString` 将返回指向只读 C 样式 null 结尾的字符串的指针。 `strcpy` 函数将 C 样式字符串的副本放入变量 `myString` 中。

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

你可以使用 `CString` 方法（例如 `SetAt`）来修改字符串对象中的单个字符。 但是，LPCTSTR 指针是临时的，当对`CString`进行任何更改时，该指针将变为无效。 `CString` 还可能超出范围，并且被自动删除。 我们建议您每次使用`CString`对象的新 LPCTSTR 指针时获取该指针。

有时你可能需要 `CString` 数据的副本以直接修改。 使用更安全的函数 `strcpy_s`（或者 Unicode/MBCS 可移植 `_tcscpy_s`）将 `CString` 对象复制到单独的缓冲区中。 这是可安全修改字符的位置，如以下示例所示。

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> （或 Unicode/MBCS-可移植`_tcscpy_s`） 的第三个参数`const wchar_t*`是 （Unicode）`const char*`或 （ANSI）。 `strcpy_s` 上面的示例为此自变量传递 `CString`。 C++ 编译器自动应用针对 `CString` 类定义的转换函数，此函数可将 `CString` 转换为 `LPCTSTR`。 定义从一种类型到另一种类型的强制转换操作的功能是 C++ 的最有用的功能之一。

## <a name="working-with-standard-run-time-library-string-functions"></a><a name="_core_working_with_standard_run.2d.time_library_string_functions"></a>使用标准运行时库字符串函数

你应该可以找到一个 `CString` 方法以执行任何字符串操作，对于此操作，你可以考虑使用标准 C 运行时库字符串函数，例如 `strcmp`（或 Unicode/MBCS 可移植 `_tcscmp`）。

如果必须使用 C 运行时字符串函数，则可以使用 _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string 中描述的技术。 你可以将 `CString` 对象复制到等效的 C 样式字符串缓冲区，在该缓冲区上执行你的操作，然后将结果 C 样式字符串分配回 `CString` 对象。

## <a name="modifying-cstring-contents-directly"></a><a name="_core_modifying_cstring_contents_directly"></a>直接修改 CString 内容

在大部分情况下，你应该使用 `CString` 成员函数修改 `CString` 对象的内容或将 `CString` 转换为 C 样式字符串。

某些情况下，直接修改 `CString` 内容很有意义，例如，在你使用需要字符缓冲区的操作系统函数时。

`GetBuffer` 和 `ReleaseBuffer` 方法提供对 `CString` 对象的内部字符缓冲区的访问权限，并使你可以直接修改它。 以下步骤介绍如何将这些函数用于此目的。

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>使用 GetBuffer 和 ReleaseBuffer 访问 CString 对象的内部字符缓冲区

1. 为 `GetBuffer` 对象调用 `CString` 并指定所需的缓冲区的长度。

1. 使用由 `GetBuffer` 返回的指针以将字符直接写入 `CString` 对象中。

1. 为 `ReleaseBuffer` 对象调用 `CString` 以更新所有内部 `CString` 状态信息，例如，字符串的长度。 直接修改 `CString` 对象的内容后，你必须在调用任何其他 `ReleaseBuffer` 成员函数前先调用 `CString`。

## <a name="using-cstring-objects-with-variable-argument-functions"></a><a name="_core_using_cstring_objects_with_variable_argument_functions"></a>使用具有可变参数函数的 CString 对象

某些 C 函数采用数量可变的自变量。 一个要注意的示例是 `printf_s`。 由于声明这种函数的方法，编译器无法确定自变量的类型，并且无法确定每个自变量上要执行何种转换操作。 因此，在将 `CString` 对象传递到采用数量可变的自变量的函数时，使用显示类型强制转换非常重要。

要在`CString`变量参数函数中使用对象，显式将强制转换为`CString`LPCTSTR 字符串，如以下示例所示。

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

## <a name="specifying-cstring-formal-parameters"></a><a name="_core_specifying_cstring_formal_parameters"></a>指定 CString 正式参数

对于需要字符串自变量的大部分函数，最好将函数原型中的形参指定为指向某个字符 (`const`) 的 `LPCTSTR` 指针，而不是 `CString`。 当正式参数指定为指向字符的`const`指针时，可以将指针传递给 TCHAR 数组、文本字符串 *`"hi there"`或`CString`对象。 该`CString`对象将自动转换为 LPCTSTR。 在可以使用 LPCTSTR 的任意位置，也可以使用`CString`对象。

如果参数不被修改，`const CString&`还可以将正式参数指定为常量字符串引用（即 ）。 如果函数将修改字符串，则删除**const**修改器。 如果需要默认的 null 值，则将其初始化为 null 字符串 [`""`]，如下所示：

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

对于大部分函数结果，你可以轻松地通过值返回 `CString` 对象。

## <a name="see-also"></a>另请参阅

[字符串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString 参数传递](../atl-mfc-shared/cstring-argument-passing.md)
