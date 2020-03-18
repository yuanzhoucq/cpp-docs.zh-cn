---
title: 使用 CArchive &lt;&lt; 并 &gt;&gt; 运算符
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442172"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt;&lt; 并 &gt;&gt; 运算符

`CArchive` 提供 <\< 和 > > 运算符，用于写入和读取文件的简单数据类型以及 `CObject`和。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>通过存档在文件中存储对象

1. 下面的示例演示如何通过存档在文件中存储对象：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>从先前存储在文件中的值加载对象

1. 下面的示例演示如何从以前存储在文件中的值加载对象：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常，你可以通过存档在 `CObject`派生类的 `Serialize` 函数中存储和加载文件，并且必须使用 DECLARE_SERIALIZE 宏进行声明。 向 `Serialize` 函数传递对 `CArchive` 对象的引用。 调用 `CArchive` 对象的 `IsLoading` 函数，以确定是否调用了 `Serialize` 函数以便从文件中加载数据或将数据存储到该文件。

可序列化 `CObject`派生类的 `Serialize` 函数通常具有以下格式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上面的代码模板与为文档的 `Serialize` 函数（从 `CDocument`派生的类）的运行时创建的模板完全相同。 此代码模板帮助你编写更易于查看的代码，因为存储代码和加载代码应始终并行，如以下示例中所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

库将 `CArchive` 的 **<\<** 和 **>>** 运算符定义为第一个操作数，将以下数据类型和类类型定义为第二个操作数：

||||
|-|-|-|
|`CObject*`|**大小**和 `CSize`|**float**|
|**WORD**|`CString`|**POINT**和 `CPoint`|
|`DWORD`|**BYTE**|`RECT` 和 `CRect`|
|**双精度**|**LONG**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  通过存档存储和加载 `CObject`需要额外考虑。 有关详细信息，请参阅[通过存档存储和加载 cobject](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

**CArchive <\<** 和 **>>** 运算符始终返回对 `CArchive` 对象的引用，该对象是第一个操作数。 这使您可以链接运算符，如下所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
