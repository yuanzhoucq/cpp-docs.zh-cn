---
title: CString 自变量传递
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317936"
---
# <a name="cstring-argument-passing"></a>CString 自变量传递

本文介绍如何将[CString](../atl-mfc-shared/reference/cstringt-class.md)对象传递到函数以及如何从函数返回`CString`对象。

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>CString 参数传递约定

定义类接口时，必须确定成员函数的参数传递约定。 有一些标准规则用于传递和返回`CString`对象。 如果按照字符串中描述的规则[为函数输入](#_core_strings_as_function_inputs)，[字符串作为函数输出](#_core_strings_as_function_outputs)，您将具有高效、正确的代码。

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>字符串作为函数输入

在调用的函数中使用`CString`对象的最有效和最安全的方法是将`CString`对象传递给函数。 尽管名称相同，`CString`但对象不会在内部存储字符串为具有空终止符的 C 样式字符串。 相反，`CString`对象会仔细跟踪其具有的字符数。 提供`CString`指向 null 终止字符串的 LPCTSTR 指针是少量工作，如果代码必须不断这样做，这些工作可能会变得重要。 结果是暂时的，`CString`因为对内容的任何更改会使 LPCTSTR 指针的旧副本无效。

在某些情况下，提供 C 样式字符串确实有意义。 例如，在 C 中写入被调用函数并且不支持对象的情况。 在这种情况下，强制参数`CString`到LPCTSTR，并且函数将获得一个 C 样式的 null 终止字符串。 还可以采用另一个方向，并使用接受 C`CString`样式字符串参数`CString`的构造函数创建对象。

如果要由函数更改字符串内容，则将参数声明为非常量`CString`引用 （`CString&`。

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>字符串作为函数输出

通常，可以从函数`CString`返回对象，因为`CString`对象遵循基元类型等值语义。 要返回只读字符串，请使用常量`CString`引用 （`const CString&`。 以下示例说明了`CString`参数和返回类型的使用：

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>另请参阅

[字符串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)
