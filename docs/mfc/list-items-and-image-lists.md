---
title: 列表项和图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: cae387dc028df46a7891e68d49f5f0c5a89126c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571036"
---
# <a name="list-items-and-image-lists"></a>列表项和图像列表

列表控件中的"项"([CListCtrl](../mfc/reference/clistctrl-class.md)) 包括图标、 标签和可能的其他信息 （在"子项"）。

列表控件项的图标包含在图像列表中。 第一个图像列表包含了图标视图中使用的全尺寸图标。 第二个可选的图像列表包含了其他控件视图中使用的相同图标的较小版本。 第三个可选的列表包含了“状态”图像，例如在某些视图中显示在小图标前面的复选框。 第四个可选的列表包含了在列表控件的单个标题项中显示的图像。

> [!NOTE]
>  如果使用 LVS_SHAREIMAGELISTS 样式创建的列表视图控件，则您有责任销毁图像列表，当它们不再被占用时。 如果您将相同的图像列表分配给多个列表视图控件，请指定此样式；否则，多个控件可能会尝试销毁同一图像列表。

有关列表项的详细信息，请参阅[列表视图图像列表](/windows/desktop/Controls/using-list-view-controls)并[项及其子项](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。 另请参阅类[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 参考*并[使用 CImageList](../mfc/using-cimagelist.md)本系列文章中。

若要创建一个列表控件，您需要提供在将新的项插入到列表中时要使用的图像列表。 下面的示例演示此过程中，其中*m_pImagelist*是类型的指针`CImageList`并*m_listctrl*是`CListCtrl`数据成员。

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

但是，如果您不打算在列表视图或列表控件中显示图标，则不需要图像列表。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

