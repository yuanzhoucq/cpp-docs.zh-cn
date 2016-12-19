---
title: "简单数据类型类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据类 [C++]"
  - "标量类 [C++]"
  - "简单数据类型类"
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 简单数据类型类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列类封装坐标绘制、字符串、时间和日期信息，从而允许使用 C\+\+ 语法的方便使用。  在类库中，这些对象可以广泛用作Windows类成员函数的参数。  由于 `CPoint`、`CSize`和 `CRect`，分别对应于 **POINT**、**SIZE**和 `RECT` 结构，在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中，您可以使用这些 C\+\+ 类对象，并使用 C 语言结构。  类通过其成员函数提供有用的接口。  `CStringT` 提供了非常灵活的动态字符串。  `CTime`、`COleDateTime`、`CTimeSpan`和 **COleTimeSpan** 对象表示日期和时间值。  有关这些类的更多信息，请参见文章 [日期和时间](../atl-mfc-shared/date-and-time.md)。  
  
 以**COle**开头的类是 由OLE 提供的数据类型的封装。  这些数据类型可在 Windows 程序中使用，不管其他 OLE 功能是否被使用。  
  
 [CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)  
 保留字符串。  
  
 [CTime](../atl-mfc-shared/reference/ctime-class.md)  
 保留绝对时间和日期的值。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE 自动化类型**DATE**的包装。  表示日期和时间值。  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 保持相对日期和时间值。  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 表示相关的 `COleDateTime` 值，如 `COleDateTime` 两个值之间的差异。  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保持坐标 \(x，y\) 对。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保持疏远，相对位置或匹配的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保留矩形区域坐标。  
  
 [C图像列表](../mfc/reference/cimagelist-class.md)  
 提供 Windows 图像列表控件的功能。  图像列表与列表控件和树控件一起使用。  它们还可以用于存储和存档一组相同大小的位图。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE 自动化类型**VARIANT**的包装。  在 **VARIANT**中可以存储多格式数据。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE 自动化类型 **CURRENCY**的包装，使用定点算术类型，小数点前 15 位和 小数点后4 位。  
  
> [!NOTE]
>  从 Visual C\+\+ .NET 开始，`CRect`、`CSize`和 `CPoint` 可以在 ATL 或 MFC 应用程序中修改。  此外，`CStringT` 中添加一独立 MFC 提供类似于 `CString`的类。  有关共享的公共类更多信息，请参见 [共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)