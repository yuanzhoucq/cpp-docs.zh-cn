---
title: 使用 CArchive &lt; &lt; 和 &gt; &gt; 运算符
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 5029227078ac0af9ebdd0c74522a7b0ae8ea4d42
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228513"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt; &lt; 和 &gt; &gt; 运算符

`CArchive`提供了 <\< and >> 的运算符，用于写入和读取文件的简单数据类型以及 `CObject` 和。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>通过存档在文件中存储对象

1. 下面的示例演示如何通过存档在文件中存储对象：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>从先前存储在文件中的值加载对象

1. 下面的示例演示如何从以前存储在文件中的值加载对象：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常，你 `Serialize` `CObject` 必须使用 DECLARE_SERIALIZE 宏声明的派生类的函数中的存档，将数据存储到文件和从文件加载数据。 向 `CArchive` 函数传递对对象的引用 `Serialize` 。 调用对象的 `IsLoading` 函数 `CArchive` 可确定函数是否已 `Serialize` 被调用，以便从文件中加载数据或将数据存储到文件中。

`Serialize`可序列化 `CObject` 的派生类的功能通常采用以下形式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上面的代码模板与为文档的函数创建的一个程序向导 `Serialize` （派生自的类）完全相同 `CDocument` 。 此代码模板帮助你编写更易于查看的代码，因为存储代码和加载代码应始终并行，如以下示例中所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

库将 **<\<** and **>>** 运算符定义为 `CArchive` 第一个操作数，将以下数据类型和类类型定义为第二个操作数：

||||
|-|-|-|
|`CObject*`|**大小**和`CSize`|**`float`**|
|**单字**|`CString`|**点**和`CPoint`|
|`DWORD`|**位**|`RECT` 和 `CRect`|
|**双精度**|**漫长**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> 通过存档存储和加载 `CObject` 需要额外考虑。 有关详细信息，请参阅[通过存档存储和加载 cobject](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

**CArchive <\<** and **> > **运算符始终返回对对象的引用，该 `CArchive` 对象是第一个操作数。 这使您可以链接运算符，如下所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另请参阅

[序列化：序列化对象](../mfc/serialization-serializing-an-object.md)
