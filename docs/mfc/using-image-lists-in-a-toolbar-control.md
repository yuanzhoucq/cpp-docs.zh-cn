---
title: 工具栏控件中使用图像列表 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76325d2b078f51860cad7fa3fab61ed7c518a41c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-image-lists-in-a-toolbar-control"></a>在工具栏控件中使用图像列表
默认情况下，使用工具栏控件中的按钮的图像存储为单个位图。 但是，你可以将按钮图像存储在图像列表的一组。 工具栏控件对象可以使用最多三个单独的映像列表：  
  
-   启用当前已启用的工具栏按钮的图像列表包含图像。  
  
-   禁用当前已禁用的工具栏按钮的图像列表包含图像。  
  
-   突出显示当前突出显示的工具栏按钮的图像列表包含图像。 工具栏使用时才使用此图像列表**TBSTYLE_FLAT**样式。  
  
 您将其与相关联时，工具栏控件将使用这些映像列表`CToolBarCtrl`对象。 此关联通过调用来实现[CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist)， [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)，和[SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)。  
  
 默认情况下，MFC 使用`CToolBar`类，以实现 MFC 应用程序工具栏。 但是，`GetToolBarCtrl`成员函数可以用于检索嵌入`CToolBarCtrl`对象。 然后可以使调用`CToolBarCtrl`使用返回的对象的成员函数。  
  
 下面的示例演示此方法通过分配已启用 (`m_ToolBarImages`) 和已禁用 (`m_ToolBarDisabledImages`) 到图像列表`CToolBarCtrl`对象 (`m_ToolBarCtrl`)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  工具栏对象使用的图像列表必须是永久的对象。 因此，它们通常是 MFC 类; 的数据成员在此示例中，主框架窗口类。  
  
 一旦与之关联图像列表`CToolBarCtrl`对象时，框架自动显示正确的按钮的图像。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

