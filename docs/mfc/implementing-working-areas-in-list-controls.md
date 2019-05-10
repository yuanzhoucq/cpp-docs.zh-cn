---
title: 实现列表控件中的工作区域
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 01b166243c9032a113d46ff297b9f6e53429da21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297211"
---
# <a name="implementing-working-areas-in-list-controls"></a>实现列表控件中的工作区域

默认情况下，列表控件排列标准网格方式中的所有项。 但是，支持另一种方法，工作区为矩形组排列的列表项。 有关实现工作区域的列表控件的映像，请参阅 Windows SDK 中使用列表视图控件。

> [!NOTE]
>  仅当列表控件处于图标或小图标模式时，工作区域是可见的。 但是，如果此视图切换到报表或列表模式，将维持任何当前工作区。

工作区域可用于显示空边框 （位于左侧、 顶部和/或项的右侧），或导致时通常不会有一个要显示的水平滚动条。 另一个常见用法是创建多个工作区域向其移动或删除项。 使用此方法，您可以具有不同的含义的单一视图中创建区域。 然后，用户无法将项分类通过将它们放置在不同区域中。 此示例将具有读/写文件的区域和另一个区域的只读的文件系统的视图。 如果文件项移动到只读的区域，它将自动变为只读的。 只读区域中的文件移动到读/写区域会使文件读/写。

`CListCtrl` 用于创建和管理在列表控件中的工作区域提供多个成员函数。 [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas)并[SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas)检索和设置的数组`CRect`对象 (或`RECT`结构)，这将存储在列表控件的当前实现中的工作区域。 此外， [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas)检索列表控件的工作区域的当前数目 （默认情况下，零）。

## <a name="items-and-working-areas"></a>项和工作区

创建工作区后，位于工作区域内的项将成为其成员。 同样，如果将项目移动到某个工作区中，它将成为移动到其中的工作区的成员。 如果项不在任何工作区中，它将自动成为第一个 （索引 0） 工作区的成员。 如果你想要创建的项目，并将其放置在特定的工作区中，将需要创建该项目，然后将其移动到通过调用所需的工作区[SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition)。 下面的第二个示例演示此技术。

下面的示例实现四个工作区域 (`rcWorkAreas`)，与每个工作区，在列表控件周围的 10 个像素宽边框的大小相等的 (`m_WorkAreaListCtrl`)。

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

在调用[ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect)进行了估算在一个区域中显示的所有项所需的总区域。 此估计值是划分为四个区域，然后使用 5 个像素宽边框填充。

下一步的示例将现有列表项分配给每个组 (`rcWorkAreas`)，并刷新的控件视图 (`m_WorkAreaListCtrl`) 以实现此效果。

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
