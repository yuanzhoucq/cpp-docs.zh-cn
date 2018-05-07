---
title: 实现列表控件中的工作区域 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44b92fbda7f00c761059a44b5bf9483e2dfac814
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-working-areas-in-list-controls"></a>实现列表控件中的工作区域
默认情况下，列表控件排列标准网格方式中的所有项。 但是，支持另一种方法，工作区，它将列表项矩形分组。 实现工作区域的列表控件的映像，请参阅 Windows SDK 中使用列表视图控件。  
  
> [!NOTE]
>  仅当列表控件处于图标或小图标模式时，工作区域是可见的。 但是，如果此视图切换到报表或列表模式，将维持任何当前工作区。  
  
 工作区域可以用于显示空边框 （在左侧、 顶部和/或项的权限），或导致水平滚动条时通常不会有一个显示。 另一个常见用法是创建多个工作区向其移动或删除项。 使用此方法，你可以具有不同的含义的单一视图中创建区域。 然后，用户无法将项分类通过将它们放置在不同的区域。 此示例将具有读/写文件的区域和另一个区域只读文件的文件系统的视图。 如果文件项已移动到只读的区域，它将自动变为只读的。 将文件从只读区域移到读/写区域会使文件读/写。  
  
 `CListCtrl` 用于创建和管理在列表控件中的工作区域中提供多个成员函数。 [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas)和[SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas)检索和设置的数组`CRect`对象 (或`RECT`结构)，其存储为列表控件的当前实现中的工作区域。 此外， [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas)检索列表控件的工作区域的当前数目 （默认情况下，零）。  
  
## <a name="items-and-working-areas"></a>项和工作区  
 创建工作区后，位于工作区中的项将成为其成员。 同样，如果的项移到某个工作区中，它将成为工作区移动到其中的成员。 如果某个项不任何工作区中，它将自动成为第一个 （索引 0） 工作区的成员。 如果你想要创建项并将其放置在特定的工作区域内，你将需要创建该项目，然后将其移到所需的工作区域，通过调用[SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition)。 下面的第二个示例演示此技术。  
  
 下面的示例实现四个的工作区域 (`rcWorkAreas`)，与每个工作区，在列表控件周围的 10 个像素宽边框的大小相等 (`m_WorkAreaListCtrl`)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]  
  
 调用[ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect)进行以获取整个区域显示在一个区域中的所有项所需的估计值。 然后，此估计值是划分为四个区域，并填充了 5 个像素宽边框。  
  
 下一个示例将现有列表项分配给每个组 (`rcWorkAreas`)，并刷新的控件视图 (`m_WorkAreaListCtrl`) 以实现此效果。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

