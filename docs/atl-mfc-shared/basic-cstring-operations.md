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
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317957"
---
# <a name="basic-cstring-operations"></a>基本 CString 操作

本主题介绍以下基本[CString](../atl-mfc-shared/reference/cstringt-class.md)操作：

- [从标准 C 文本字符串创建 CString 对象](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [访问 CString 中的单个字符](#_core_accessing_individual_characters_in_a_cstring)

- [串联两个 CString 对象](#_core_concatenating_two_cstring_objects)

- [比较 CString 对象](#_core_comparing_cstring_objects)

- [转换 CString 对象](#_core_converting_cstring_objects)

`Class CString`基于类模板[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)。 `CString`是`CStringT`**的类型定义**。 更确切地说`CString`，是`CStringT`的*显式专门化*的类型**定义**，这是使用类模板定义类的常用方法。 同样定义的类是`CStringA``CStringW`和 。

`CString``CStringA`，并在`CStringW`atlstr.h 中定义。 `CStringT`在 cstringt.h 中定义。

`CString`，`CStringA`每个`CStringW`获取一组定义`CStringT`的方法和运算符，以便与它们支持的字符串数据一起使用。 有些方法重复，在某些情况下，超过了 C 运行时库的字符串服务。

注意：`CString`是本机类。 对于用于C++/CLI 托管项目中的字符串类，请使用`System.String`。

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>从标准 C 文本字符串创建 CString 对象

您可以将 C 样式文本字符串分配给 a，`CString`就像您可以将一个对象`CString`分配给另一个对象一样。

- 将 C 文本字符串的值分配给`CString`对象。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 将一个`CString`对象的值分配给另`CString`一个对象。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   当一个对象`CString`分配给另一个`CString`对象时，将复制对象的内容。 因此，这两个字符串不共享对构成字符串的实际字符的引用。 有关如何将对象用作`CString`值的详细信息，请参阅[CString 语义](../atl-mfc-shared/cstring-semantics.md)。

   > [!NOTE]
   > 编写应用程序以便可以编译为 Unicode 或 ANSI，请使用_T宏编写文本字符串。 有关详细信息，请参阅[Unicode 和多字节字符集 （MBCS） 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>访问 CString 中的单个字符

可以使用 和 方法访问对象`CString``GetAt``SetAt`中的单个字符。 您还可以使用数组元素或下标运算符 （ * ） 而不是`GetAt`获取单个字符。 （这类似于按索引访问数组元素，如标准 C 样式字符串中。字符的`CString`索引值是零基的。

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>串联两个 CString 对象

要串联两`CString`个对象，请使用串联运算符 （* 或 *），如下所示。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

对串联运算符（* 或 +）的至少一个`CString`参数必须是对象，但可以使用常量字符串（例如`"big"`）或**字符**（例如，"x"）作为另一个参数。

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>比较 CString 对象

方法和`Compare`* 运算符`CString`等效。 `Compare`，**运算符 =**，`CompareNoCase`并且是 MBCS 和 Unicode 感知;`CompareNoCase`也区分大小写。 的方法`Collate``CString`对区域设置敏感，通常比 慢`Compare`。 仅在`Collate`必须遵守当前区域设置指定的排序规则的情况下使用。

下表显示了 C 运行时库中可用的[CString](../atl-mfc-shared/reference/cstringt-class.md)比较函数及其等效的 Unicode/MBCS 可移植函数。

|CString 函数|MBCS 功能|Unicode 函数|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

类`CStringT`模板定义关系运算符（<、*、>\<*、>、*和 ！"），这些运算符可供`CString`使用。 您可以使用这些运算符比较`CStrings`两个，如以下示例所示。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>转换 CString 对象

有关将 CString 对象转换为其他字符串类型的信息，请参阅[如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)。

## <a name="using-cstring-with-wcout"></a>将 CString 与 wcout 一起使用

要将 CString`wcout`与 一起使用，必须显式将`const wchar_t*`对象强制转换为 a，如以下示例所示：

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

如果没有强制转换，`cs`将被视为 并`void*``wcout`打印对象的地址。 此行为是由模板参数推导和重载解析之间的微妙交互引起的，这些交互本身是正确的，并且符合C++标准。

## <a name="see-also"></a>另请参阅

[字符串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[模板专业化](../cpp/template-specialization-cpp.md)<br/>
[如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)
