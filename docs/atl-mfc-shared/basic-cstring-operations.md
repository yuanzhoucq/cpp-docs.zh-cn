---
title: 基本 CString 操作
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: fa46e82f19d87c49f652779d0e86e78549935965
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220894"
---
# <a name="basic-cstring-operations"></a>基本 CString 操作

本主题介绍以下基本[CString](../atl-mfc-shared/reference/cstringt-class.md)操作：

- [从标准 C 文本字符串创建 CString 对象](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [访问 CString 中的单个字符](#_core_accessing_individual_characters_in_a_cstring)

- [串联两个 CString 对象](#_core_concatenating_two_cstring_objects)

- [比较 CString 对象](#_core_comparing_cstring_objects)

- [转换 CString 对象](#_core_converting_cstring_objects)

`Class CString`基于类模板[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)。 `CString`是 **`typedef`** 的 `CStringT` 。 更准确地 `CString` 说，是 **`typedef`** 的*显式专用化* `CStringT` ，这是使用类模板来定义类的常用方法。 同样定义的类为 `CStringA` 和 `CStringW` 。

`CString`、 `CStringA` 和 `CStringW` 在 atlstr.h 中定义。 `CStringT`在 cstringt 中定义。

`CString`、 `CStringA` 和 `CStringW` 都将获取一组由定义的方法和运算符， `CStringT` 以与它们支持的字符串数据一起使用。 某些方法是重复的，并且在某些情况下，超过 C 运行时库的字符串服务。

注意： `CString` 是一个本机类。 对于在 c + +/CLI 托管项目中使用的字符串类，请使用 `System.String` 。

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>从标准 C 文本字符串创建 CString 对象

可以将 C 样式文本字符串分配给， `CString` 就像可以将一个对象分配 `CString` 给另一个对象一样。

- 将 C 文本字符串的值分配给 `CString` 对象。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 将一个值分配 `CString` 给另一个 `CString` 对象。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   将 `CString` 一个对象分配给另一个对象时，会复制对象的内容 `CString` 。 因此，这两个字符串不会共享对构成字符串的实际字符的引用。 有关如何使用 `CString` 对象作为值的详细信息，请参阅[CString 语义](../atl-mfc-shared/cstring-semantics.md)。

   > [!NOTE]
   > 编写应用程序，以便可以使用 _T 宏为 Unicode 或 ANSI 的代码文本字符串编译该应用程序。 有关详细信息，请参阅[Unicode 和多字节字符集（MBCS）支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>访问 CString 中的单个字符

您可以 `CString` 使用和方法访问对象中的单个字符 `GetAt` `SetAt` 。 你还可以使用数组元素或下标运算符（[]）而不是 `GetAt` 来获取单个字符。 （这类似于通过索引访问数组元素，如标准 C 样式字符串中所示。）字符的索引值 `CString` 从0开始。

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>串联两个 CString 对象

若要连接两个 `CString` 对象，请使用串联运算符（+ 或 + =），如下所示。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

连接运算符（+ 或 + =）的至少一个参数必须是 `CString` 对象，但对于其他参数，可以使用常量字符串（例如， `"big"` ）或 a **`char`** （例如 "x"）。

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>比较 CString 对象

的 `Compare` 方法和 = = 运算符 `CString` 等效。 `Compare`、 **operator = =** 和 `CompareNoCase` 是 MBCS 和 Unicode 感知的; `CompareNoCase` 也不区分大小写。 的 `Collate` 方法 `CString` 是区分区域设置的，并且通常比更慢 `Compare` 。 仅使用由 `Collate` 当前区域设置指定的排序规则必须遵守的位置。

下表显示了可用的[CString](../atl-mfc-shared/reference/cstringt-class.md)比较函数以及它们在 C 运行时库中的等效 UNICODE/MBCS 可移植函数。

|CString 函数|MBCS 函数|Unicode 函数|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`类模板定义可供使用的关系运算符（<、 \<=, > =、>、= = 和！ =） `CString` 。 您可以 `CStrings` 使用这些运算符比较两个，如下面的示例中所示。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>转换 CString 对象

有关将 CString 对象转换为其他字符串类型的信息，请参阅[如何：在各种字符串类型之间转换](../text/how-to-convert-between-various-string-types.md)。

## <a name="using-cstring-with-wcout"></a>在 wcout 中使用 CString

若要将 CString 用于 `wcout` ，必须将对象显式强制转换为， `const wchar_t*` 如以下示例中所示：

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

在不进行强制转换的情况下， `cs` 将被视为 **`void*`** 并 `wcout` 输出对象的地址。 此行为是由模板参数推导和重载解析之间的细微交互引起的，它们自身正确并符合 c + + 标准。

## <a name="see-also"></a>另请参阅

[字符串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[模板专用化](../cpp/template-specialization-cpp.md)<br/>
[如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)
