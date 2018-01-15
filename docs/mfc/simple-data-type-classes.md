---
title: "简单数据类型类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.data
dev_langs: C++
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2b4df05d64cb97032477ca50ff4b0ce572829b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="simple-data-type-classes"></a>简单数据类型类
下列类封装绘制坐标、字符串以及时间和日期信息，从而能够方便地使用 C++ 语法。 这些对象将作为参数广泛用于类库中 Windows 类的成员函数。 因为`CPoint`， `CSize`，和`CRect`对应于**点**，**大小**，和`RECT`结构，分别在 Windows SDK 中，你可以使用这些对象C + + 类只要你可以使用这些 C 语言结构。 这些类通过其成员函数提供有用的接口。 `CStringT` 提供了非常灵活的动态字符串。 `CTime``COleDateTime`， `CTimeSpan`，和**COleTimeSpan**表示时间和日期值。 有关这些类的详细信息，请参阅文章[日期和时间](../atl-mfc-shared/date-and-time.md)。  
  
 开头的类"**COle**"是由 OLE 提供的数据类型的封装。 这些数据类型可在 Windows 程序中使用，而不管是否使用其他 OLE 功能。  
  
 [CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)  
 保留字符串。  
  
 [CTime](../atl-mfc-shared/reference/ctime-class.md)  
 保留绝对时间和日期值。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE 自动化类型的包装**日期**。 表示日期和时间值。  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 保留相对时间和日期值。  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 保留相对 `COleDateTime` 值，如两个 `COleDateTime` 值之间的差异。  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保留坐标 (x, y) 对。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保留距离、相对位置或匹配的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保留矩形区域的坐标。  
  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 提供 Windows 图像列表的功能。 图像列表将与列表控件和树控件一起使用。 它们还可以用于存储和存档一组大小相同的位图。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE 自动化类型的包装**VARIANT**。 中的数据**VARIANT**可用多种格式存储。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE 自动化类型的包装**货币**，定点算数类型，有 15 位，小数点前的小数点后的有 4 位。  
  
> [!NOTE]
>  `CRect``CSize`，和`CPoint`ATL 或 MFC 应用程序中可用。 此外，`CStringT`提供了 MFC 独立`CString`-与类一样。 有关共享实用程序类的详细信息，请参阅[共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

