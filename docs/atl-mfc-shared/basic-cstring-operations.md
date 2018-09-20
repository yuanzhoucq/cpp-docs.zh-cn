---
title: 基本 CString 操作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab2c857451e399e56e69d79240d4ace023a8b301
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424074"
---
# <a name="basic-cstring-operations"></a>基本 CString 操作

本主题介绍了以下基本[CString](../atl-mfc-shared/reference/cstringt-class.md)操作：

- [从标准 C 文本字符串创建 CString 对象](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [访问 CString 中的单个字符](#_core_accessing_individual_characters_in_a_cstring)

- [串联两个 CString 对象](#_core_concatenating_two_cstring_objects)

- [将 CString 对象进行比较](#_core_comparing_cstring_objects)

- [将 CString 对象转换](#_core_converting_cstring_objects)

`Class CString` 类模板为基础[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)。 `CString` 是**typedef**的`CStringT`。 更准确地说`CString`是**typedef**的*显式专用化*的`CStringT`，这是使用类模板定义的类的常用方法。 同样定义的类是`CStringA`和`CStringW`。

`CString``CStringA`，和`CStringW`atlstr.h 中定义。 `CStringT` cstringt.h 中定义。

`CString``CStringA`，并`CStringW`每个获取一组方法和运算符定义的`CStringT`与它们支持的字符串数据一起使用。 某些方法重复的并在某些情况下，超过 C 运行时库的字符串服务。

注意：`CString`是本机类。 字符串类，用于在 C + + /cli CLI 托管项目中，使用`System.String`。

##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> 从标准 C 文本字符串创建 CString 对象

可以将分配到 C 样式字符串`CString`正如您可以指定一个`CString`到另一个对象。

- 到 C 文本字符串的值分配为`CString`对象。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 一个值分配`CString`到另一个`CString`对象。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   内容`CString`对象复制时一个`CString`对象分配给另一个。 因此，两个字符串不共享的实际字符组成的字符串的引用。 有关如何使用详细信息`CString`对象作为值，请参阅[CString 语义](../atl-mfc-shared/cstring-semantics.md)。

   > [!NOTE]
   > 若要编写您的应用程序，使其可以编译为 Unicode 或 ANSI，通过使用 _T 宏代码文本字符串。 有关详细信息，请参阅[Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> 访问 CString 中的单个字符

您可以访问中的单个字符`CString`通过使用对象`GetAt`和`SetAt`方法。 此外可以使用数组元素中，或下标运算符 ([])，而不是`GetAt`来获取单个字符。 （这类似于访问数组元素的索引，如标准的 C 样式字符串中所示。）索引值`CString`字符是从零开始。

##  <a name="_core_concatenating_two_cstring_objects"></a> 串联两个 CString 对象

要串联两个`CString`对象，请使用串联运算符 (+ 或 + =)，按如下所示。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

至少一个参数的串联运算符 (+ 或 + =) 必须是`CString`对象，但你可以使用字符常量字符串 (例如， `"big"`) 或**char** (例如，x) 的其他参数。

##  <a name="_core_comparing_cstring_objects"></a> 将 CString 对象进行比较

`Compare`方法和 = = 运算符`CString`是等效的。 `Compare`**运算符 = =**，和`CompareNoCase`可识别 MBCS 和 Unicode;`CompareNoCase`也是不区分大小写。 `Collate`方法`CString`区分区域设置的并且通常比速度慢`Compare`。 使用`Collate`按当前区域设置指定仅在其中你必须遵守的排序规则。

下表显示了可用[CString](../atl-mfc-shared/reference/cstringt-class.md)比较函数和其等效的 Unicode/MBCS 可移植函数 C 运行时库中。

|CString 函数|MBCS 函数|Unicode 函数|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`类模板定义了关系运算符 (<， \<=、 > =、 >、 = =、 和 ！ =)，这是可供使用`CString`。 您可以比较两个`CStrings`使用这些运算符，如下面的示例中所示。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

##  <a name="_core_converting_cstring_objects"></a> 将 CString 对象转换

有关将 CString 对象转换为其他字符串类型的信息，请参阅[如何： 转换类型之间的各种字符串](../text/how-to-convert-between-various-string-types.md)。

## <a name="using-cstring-with-wcout"></a>Wcout 使用 CString

若要使用与 CString`wcout`必须显式强制转换到的对象`const wchar_t*`如下面的示例中所示：

```
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;

```

无需转换，`cs`被视为`void*`和`wcout`打印对象的地址。 此行为是由 c + + 标准模板参数推导和重载解析中正确本身，并且符合之间进行细微交互引起的。

## <a name="see-also"></a>请参阅

[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[模板特殊化](../cpp/template-specialization-cpp.md)<br/>
[如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)

