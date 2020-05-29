---
title: 实现列表控件中的工作区域
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377213"
---
# <a name="implementing-working-areas-in-list-controls"></a>实现列表控件中的工作区域

默认情况下，列表控件以标准网格方式排列所有项目。 但是，支持另一种方法，工作区，将列表项排列到矩形组中。 有关实现工作区的列表控件的图像，请参阅在 Windows SDK 中使用列表视图控件。

> [!NOTE]
> 仅当列表控件处于图标或小图标模式时，工作区才可见。 但是，如果视图切换到报表或列表模式，则维护任何当前工作区。

工作区可用于显示空边框（在项目的左侧、顶部和/或右侧），或在通常不存在水平滚动条时导致显示水平滚动条。 另一个常见用法是创建多个工作区，以便可以移动或删除项目。 使用此方法，您可以在单个视图中创建具有不同含义的区域。 然后，用户可以通过将项目放置在其他区域来对项目进行分类。 例如，文件系统的视图具有读取/写入文件的区域和另一个只读文件区域。 如果将文件项移动到只读区域，它将自动变为只读。 将文件从只读区域移动到读/写区域将使文件被读/写。

`CListCtrl`提供了多个成员函数，用于在列表控件中创建和管理工作区。 [GetWork区域](../mfc/reference/clistctrl-class.md#getworkareas)和[SetWork区域](../mfc/reference/clistctrl-class.md#setworkareas)检索和设置`CRect`对象（或结构）`RECT`数组，这些对象（或结构）存储当前实现的工作区域，以便进行列表控制。 此外[，GetNumberOfWork区域](../mfc/reference/clistctrl-class.md#getnumberofworkareas)会检索列表控件的当前工作区数（默认情况下为零）。

## <a name="items-and-working-areas"></a>项目和工作区域

创建工作区时，位于工作区内的项将成为工作区的成员。 同样，如果项目移动到工作区，它将成为移动到工作区的成员。 如果项目不位于任何工作区中，它将自动成为第一个 （索引 0） 工作区的成员。 如果要创建项并将其放置在特定工作区中，则需要创建该项，然后将其移动到所需的工作区中，并调用[SetItemMove](../mfc/reference/clistctrl-class.md#setitemposition)。 下面的第二个示例演示了此技术。

下面的示例在每个工作区周围实现四个`rcWorkAreas`大小相等的工作区域 （），每个工作区周围都有 10 像素宽的边框，在列表控件`m_WorkAreaListCtrl`（） 中。

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

调用[近似视图Rect](../mfc/reference/clistctrl-class.md#approximateviewrect)是为了获得显示一个区域中所有项目所需的总面积的估计值。 然后，此估计值分为四个区域，并填充了 5 像素宽的边框。

下一个示例将现有列表项分配给每个组 （`rcWorkAreas`）， 并刷新控件视图`m_WorkAreaListCtrl`（ ） 以完成效果。

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
