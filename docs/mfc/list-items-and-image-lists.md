---
title: 列表项和图像列表 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6bd7a97330a8a646a880bf229562dbec9a70181
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349108"
---
# <a name="list-items-and-image-lists"></a>列表项和图像列表
列表控件中的"项"([CListCtrl](../mfc/reference/clistctrl-class.md)) 图标、 标签和可能的其他信息 （在"子项"） 组成。  
  
 列表控件项的图标包含在图像列表中。 第一个图像列表包含了图标视图中使用的全尺寸图标。 第二个可选的图像列表包含了其他控件视图中使用的相同图标的较小版本。 第三个可选的列表包含了“状态”图像，例如在某些视图中显示在小图标前面的复选框。 第四个可选的列表包含了在列表控件的单个标题项中显示的图像。  
  
> [!NOTE]
>  如果列表视图控件是使用 `LVS_SHAREIMAGELISTS` 样式创建的，则您负责在不再使用图像列表时将其销毁。 如果您将相同的图像列表分配给多个列表视图控件，请指定此样式；否则，多个控件可能会尝试销毁同一图像列表。  
  
 关于列表项的详细信息，请参阅[列表视图图像列表](http://msdn.microsoft.com/library/windows/desktop/bb774736)和[项及其子项](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。 另请参阅类[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 参考*和[使用 CImageList](../mfc/using-cimagelist.md)此系列文章中。  
  
 若要创建一个列表控件，您需要提供在将新的项插入到列表中时要使用的图像列表。 以下示例演示了此过程，其中的 `m_pImagelist` 是 `CImageList` 类型的指针，`m_listctrl` 是 `CListCtrl` 数据成员。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 但是，如果您不打算在列表视图或列表控件中显示图标，则不需要图像列表。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

