---
title: 实现列表控件中的工作区域
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: abbf9dd823e13fab252b7af8f32338b0d801079b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626377"
---
# <a name="implementing-working-areas-in-list-controls"></a>实现列表控件中的工作区域

默认情况下，列表控件以标准网格方式排列所有项。 但是，支持另一种方法，即工作区域，将列表项排列成矩形组。 对于实现工作区域的列表控件的图像，请参阅在 Windows SDK 中使用列表视图控件。

> [!NOTE]
> 只有列表控件处于图标或小图标模式时，工作区才可见。 但是，如果视图切换到报表或列表模式，则将保留任何当前工作区。

工作区可用于显示空边框（在项的左侧、顶部和/或右侧），或在正常情况下不会显示水平滚动条。 另一种常见用途是创建多个工作区，可将项移动或删除。 使用此方法，您可以在具有不同含义的单个视图中创建区域。 然后，用户可以通过将其放在不同的区域来对其进行分类。 这种情况的一个示例是文件系统的一个视图，其中包含读/写文件区域和只读文件的另一个区域。 如果文件项已移动到只读区域，则会自动变为只读。 将文件从只读区域移到读取/写入区域会使文件成为读/写文件。

`CListCtrl`提供了几个用于创建和管理列表控件中的工作区域的成员函数。 [GetWorkAreas](reference/clistctrl-class.md#getworkareas)和[SetWorkAreas](reference/clistctrl-class.md#setworkareas)检索和设置 `CRect` 对象（或 `RECT` 结构）的数组，该数组存储当前为列表控件实现的工作区。 此外， [GetNumberOfWorkAreas](reference/clistctrl-class.md#getnumberofworkareas)还会检索列表控件的当前工作区域数（默认情况下为零）。

## <a name="items-and-working-areas"></a>项和工作区

在创建工作区时，位于工作区内的项将成为该工作区的成员。 同样，如果将项移动到工作区域，则该项将成为它移动到的工作区的成员。 如果某个项不在任何工作区域内，则它将自动成为第一个（索引为0）工作区的成员。 如果要创建一个项并将其置于特定的工作区域，则需要创建该项，并通过调用[SetItemPosition](reference/clistctrl-class.md#setitemposition)将其移到所需的工作区中。 下面的第二个示例演示了此方法。

下面的示例 `rcWorkAreas` 在列表控件（）的每个工作区周围实现大小相等且大小为10个像素的工作区（） `m_WorkAreaListCtrl` 。

[!code-cpp[NVC_MFCControlLadenDialog#20](codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

已对[ApproximateViewRect](reference/clistctrl-class.md#approximateviewrect)进行调用，以估计显示一个区域中的所有项所需的总区域数。 然后，将此估算分为四个区域，并用5个像素宽的边框进行填充。

下一个示例将现有列表项分配给每个组（ `rcWorkAreas` ）并刷新控件视图（ `m_WorkAreaListCtrl` ）以完成效果。

[!code-cpp[NVC_MFCControlLadenDialog#21](codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](using-clistctrl.md)<br/>
[控件](controls-mfc.md)
