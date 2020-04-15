---
title: 简单数据类型类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365401"
---
# <a name="simple-data-type-classes"></a>简单数据类型类

下列类封装绘制坐标、字符串以及时间和日期信息，从而能够方便地使用 C++ 语法。 这些对象将作为参数广泛用于类库中 Windows 类的成员函数。 因为`CPoint` `CSize`，`CRect`和 对应于 Windows SDK 中的**POINT、SIZE**和**RECT**结构，因此无论使用这些 C 语言结构，都可以使用这些C++类的对象。 **SIZE** 这些类通过其成员函数提供有用的接口。 `CStringT` 提供了非常灵活的动态字符串。 `CTime``COleDateTime`，`CTimeSpan`表示`COleTimeSpan`时间和日期值。 有关这些类的详细信息，请参阅文章["日期和时间](../atl-mfc-shared/date-and-time.md)"。

以""`COle`开头的类是 OLE 提供的数据类型的封装。 这些数据类型可在 Windows 程序中使用，而不管是否使用其他 OLE 功能。

[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)<br/>
保留字符串。

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
保留绝对时间和日期值。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 自动化类型**DATE**的包装器 。 表示日期和时间值。

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
保留相对时间和日期值。

[COleDatetimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
保留相对 `COleDateTime` 值，如两个 `COleDateTime` 值之间的差异。

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
保留坐标 (x, y) 对。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
保留距离、相对位置或匹配的值。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
保留矩形区域的坐标。

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
提供 Windows 图像列表的功能。 图像列表将与列表控件和树控件一起使用。 它们还可以用于存储和存档一组大小相同的位图。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE 自动化类型**VARIANT**的包装器 。 **VARIANT**中的数据可以以多种格式存储。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE 自动化类型**货币**的包装器，一种定点算术类型，在小数点之前有 15 位数字，后为 4 位。

> [!NOTE]
> `CRect``CSize`，`CPoint`并且可用于 ATL 或 MFC 应用程序。 此外，`CStringT`还提供与 MFC 无关`CString`的类。 有关共享实用程序类的详细信息，请参阅[共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
