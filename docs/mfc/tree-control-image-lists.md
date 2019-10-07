---
title: 树控件图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 8f9e323244657ea6a7cc132deab6deedfcd1a167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513369"
---
# <a name="tree-control-image-lists"></a>树控件图像列表

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 中的每一项都可以有一对关联的位图图像。 图像显示在项标签的左侧。 选择项时, 将显示一个图像, 而当项处于未选中状态时显示另一个图像。 例如, 当某个项处于选中状态时, 它可能会显示一个打开的文件夹, 并显示未选择的关闭文件夹。

若要使用项映像, 必须通过构造[CImageList](../mfc/reference/cimagelist-class.md)对象并使用[CImageList:: create](../mfc/reference/cimagelist-class.md#create)函数创建关联的图像列表来创建一个图像列表。 然后, 将所需的位图添加到列表中, 并通过使用[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)成员函数将该列表与树控件相关联。 默认情况下, 所有项均显示所选和 nonselected 状态的图像列表中的第一个图像。 通过使用[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成员函数向树控件添加项时, 可以通过指定选定图像和 nonselected 图像的索引来更改特定项的默认行为。 使用[SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)成员函数添加项后, 可以更改索引。

树控件的图像列表还可以包含覆盖图像, 这些图像设计用于叠加到项图像上。 树控件项状态的位8到11中的非零值指定覆盖图像的从1开始的索引 (0 表示无覆盖图像)。 由于使用的是4位的基于1的索引, 覆盖映像必须位于图像列表中的前15个图像内。 有关树控件项状态的详细信息, 请参阅本主题前面的[树控件项状态概述](../mfc/tree-control-item-states-overview.md)。

如果指定了状态图像列表, 则树控件会在状态图像的每个项的图标左侧保留空间。 应用程序可以使用状态图像 (如选中和清除的复选框) 来指示应用程序定义的项状态。 0到15位的非零值指定状态图像的从1开始的索引 (0 表示无状态图像)。

通过指定**I_IMAGECALLBACK**值 (而不是映像的索引), 可以延迟指定所选的或 nonselected 的图像, 直到重绘该项为止。 **I_IMAGECALLBACK**通过发送[TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo)通知消息指示树控件查询索引的应用程序。

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)成员函数检索树控件图像列表的句柄。 如果需要向列表中添加更多图像, 此函数很有用。 有关图像列表的详细信息, 请参阅[使用 CImageList](../mfc/using-cimagelist.md)、 [CImageList](../mfc/reference/cimagelist-class.md) in *MFC Reference*和 Windows SDK 中的[图像列表](/windows/win32/controls/image-lists)。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
