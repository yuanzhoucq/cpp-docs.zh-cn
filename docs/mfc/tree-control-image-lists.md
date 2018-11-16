---
title: 树控件图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: e42e601fbf803f8ccfe359a10664149ac8f11086
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693240"
---
# <a name="tree-control-image-lists"></a>树控件图像列表

树控件中的每个项 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 可以有与之关联的位图化图像的对。 在左侧和右侧的项的标签上显示图像。 选择该项，和其他显示当未选定项时，会显示一个图像。 例如，某一项可能显示为选中状态时打开的文件夹和关闭的文件夹未选中状态时。

若要使用项映像，必须创建图像列表通过构造[CImageList](../mfc/reference/cimagelist-class.md)对象，并使用[CImageList::Create](../mfc/reference/cimagelist-class.md#create)函数来创建关联的图像列表。 然后将所需的位图添加到列表中，并将列表与树控件相关联的使用[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)成员函数。 默认情况下，所有项在选定和未选定状态的图像列表中都显示的第一个图像。 可以通过将项添加到使用树控件时指定选定和未选定图像的索引更改的特定项的默认行为[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成员函数。 您可以通过使用添加项后更改索引[SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage)成员函数。

树控件的图像列表还可以包含覆盖图像，它们可叠加在项图像。 中的树控件项状态的 8 到 11 位非零值指定覆盖图像的基于 1 的索引 （0 表示没有覆盖图像）。 由于使用 4 位的基于 1 的索引，则必须在图像列表中的前 15 个映像之间是覆盖图像。 树控件项状态的详细信息，请参阅[树控件项状态概述](../mfc/tree-control-item-states-overview.md)本主题前面的。

如果指定状态图像列表，则树控件中保留的状态图像的每个项的图标左侧的空间。 应用程序可以使用状态图像，如选中和清除复选框，以指示应用程序定义的项状态。 一个非零值以 12 到 15 位为单位指定状态图像的基于 1 的索引 （0 表示没有状态图像）。

通过指定**I_IMAGECALLBACK**值而不是图像的索引，您可以延迟直到项目将为要重新绘制指定的所选或原样映像。 **I_IMAGECALLBACK**指示树控件来查询索引的应用程序通过发送[TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo)通知消息。

[GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist)成员函数将检索树控件的图像列表的句柄。 此函数很有用，如果您需要将更多映像添加到列表。 有关图像列表的详细信息，请参阅[使用 CImageList](../mfc/using-cimagelist.md)， [CImageList](../mfc/reference/cimagelist-class.md)中*MFC 参考*，以及[图像列表](/windows/desktop/controls/image-lists)中Windows SDK。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

