---
title: 列表项和图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: d378c6e07280349f9995981ad794039ebc015b25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353053"
---
# <a name="list-items-and-image-lists"></a>列表项和图像列表

列表控件中的"项" （[CListCtrl](../mfc/reference/clistctrl-class.md)） 由图标、标签和可能的其他信息（在"子项"中）组成。

列表控件项的图标包含在图像列表中。 第一个图像列表包含了图标视图中使用的全尺寸图标。 第二个可选的图像列表包含了其他控件视图中使用的相同图标的较小版本。 第三个可选的列表包含了“状态”图像，例如在某些视图中显示在小图标前面的复选框。 第四个可选的列表包含了在列表控件的单个标题项中显示的图像。

> [!NOTE]
> 如果使用LVS_SHAREIMAGELISTS样式创建列表视图控件，则负责在图像列表不再使用时销毁它们列表。 如果您将相同的图像列表分配给多个列表视图控件，请指定此样式；否则，多个控件可能会尝试销毁同一图像列表。

有关列表项的详细信息，请参阅 Windows SDK 中的["列表查看图像列表](/windows/win32/Controls/using-list-view-controls)"和["项目和子项目](/windows/win32/Controls/using-list-view-controls)"。 此外，请参阅*MFC 参考*中的类[CImageList，](../mfc/reference/cimagelist-class.md)并在此系列文章中[使用 CImageList。](../mfc/using-cimagelist.md)

若要创建一个列表控件，您需要提供在将新的项插入到列表中时要使用的图像列表。 下面的示例演示了此过程，其中*m_pImagelist*是类型的`CImageList`指针 *，m_listctrl*是`CListCtrl`数据成员。

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

但是，如果您不打算在列表视图或列表控件中显示图标，则不需要图像列表。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
