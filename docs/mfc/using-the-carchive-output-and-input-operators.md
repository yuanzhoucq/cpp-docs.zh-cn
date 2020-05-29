---
title: 使用 CArchive &lt; &lt; &gt;&gt;和运算符
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368964"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt; &lt; &gt;&gt;和运算符

`CArchive`提供<\<和 >> 运算符，用于编写和读取简单的数据类型以及`CObject`从文件进行和读取。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>通过存档将对象存储在文件中

1. 下面的示例演示如何通过存档将对象存储在文件中：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>从以前存储在文件中的值加载对象

1. 下面的示例演示如何从以前存储在文件中的值加载对象：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常，在派生类`Serialize`的`CObject`函数中，通过存档存储和加载数据，并且必须使用DECLARE_SERIALIZE宏声明。 对`CArchive`对象的引用传递给函数`Serialize`。 调用`IsLoading``CArchive`对象的函数以确定是否已调用`Serialize`函数以将数据从文件加载或将数据存储到文件中。

可`Serialize``CObject`序列化派生类的函数通常具有以下形式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上述代码模板与 AppWizard 为文档`Serialize`的函数（派生自`CDocument`的类）创建的一个代码模板完全相同。 此代码模板可帮助您编写更易于查看的代码，因为存储代码和加载代码应始终并行，如以下示例所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

库将 第**<** 一**>>** 个操作`CArchive`数和运算符定义为第一个操作数，以下数据类型和类类型定义为第二个操作数：

||||
|-|-|-|
|`CObject*`|**尺寸**和`CSize`|**浮动**|
|**WORD**|`CString`|**点**和`CPoint`|
|`DWORD`|**字节**|`RECT` 和 `CRect`|
|**双精度**|**长**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> 通过存档存储`CObject`和加载 s 需要额外考虑。 有关详细信息，请参阅[通过存档存储和加载 CObjects。](../mfc/storing-and-loading-cobjects-via-an-archive.md)

**CArchive<\<** 和**>>** 运算符始终返回对`CArchive`对象的引用，这是第一个操作数。 这使您能够链接运算符，如下图所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
