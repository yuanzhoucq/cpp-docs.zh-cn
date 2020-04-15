---
title: 使用 CComBSTR 进行编程 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321793"
---
# <a name="programming-with-ccombstr-atl"></a>使用 CComBSTR 进行编程 (ATL)

ATL 类[CComBSTR](../atl/reference/ccombstr-class.md)提供围绕 BSTR 数据类型的包装器。 虽然`CComBSTR`是一个有用的工具，但有几个情况需要谨慎。

- [转换问题](#programmingwithccombstr_conversionissues)

- [范围问题](#programmingwithccombstr_scopeissues)

- [显式释放 CComBSTR 对象](#programmingwithccombstr_explicitlyfreeing)

- [在循环中使用 CComBSTR 对象](#programmingwithccombstr_usingloops)

- [内存泄漏问题](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>转换问题

尽管多`CComBSTR`种方法将自动将 ANSI 字符串参数转换为 Unicode，但这些方法将始终返回 Unicode 格式字符串。 要将输出字符串转换回 ANSI，请使用 ATL 转换类。 有关 ATL 转换类的详细信息，请参阅[ATL 和 MFC 字符串转换宏](reference/string-conversion-macros.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

如果使用字符串文本来修改`CComBSTR`对象，请使用宽字符串。 这将减少不必要的转换。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>范围问题

与任何表现良好的类一样，当它超出范围`CComBSTR`时，它将释放其资源。 如果函数返回指向字符串的`CComBSTR`指针，则可能会导致问题，因为指针将引用已释放的内存。 在这些情况下，请使用 方法，`Copy`如下所示。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>显式释放 CComBSTR 对象

在对象超出作用域之前，`CComBSTR`可以显式释放对象中包含的字符串。 如果释放字符串，则`CComBSTR`该对象无效。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>在循环中使用 CComBSTR 对象

由于`CComBSTR`类分配缓冲区以执行某些操作（如`+=`运算符或`Append`方法），因此不建议在紧密循环内执行字符串操作。 在这些情况下，`CStringT`提供更好的性能。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>内存泄漏问题

将初始`CComBSTR`化的地址作为 **[out]** 参数传递给函数会导致内存泄漏。

在下面的示例中，当函数`"Initialized"``MyGoodFunction`替换字符串时，分配给保存字符串的字符串将泄露。

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

为避免泄漏，请在现有`Empty``CComBSTR`对象上调用方法，然后再将地址作为 **[out]** 参数传递。

请注意，如果函数的参数**为 [在，出]，** 则相同的代码不会导致泄漏。

## <a name="see-also"></a>另请参阅

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[字符串转换宏](../atl/reference/string-conversion-macros.md)
