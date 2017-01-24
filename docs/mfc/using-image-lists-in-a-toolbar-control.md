---
title: "在工具栏控件中使用图像列表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl 类, 图像列表"
  - "图像列表 [C++], 工具栏控件"
  - "工具栏控件 [MFC], 图像"
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在工具栏控件中使用图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，按钮使用的图像在工具栏控件存储为单个位图。  但是，也可以存储在一个组的按钮图像图像列表。  工具栏控件可以使用三个对象不同图像列表：  
  
-   启用的图像列表包含当前已启用工具栏的按钮图像。  
  
-   禁用的图像列表包含当前禁用的工具栏按钮的图像。  
  
-   突出显示的图像列表包含当前突出显示的工具栏按钮的图像。  此图像列表，在工具栏使用 **TBSTYLE\_FLAT** 样式时，请使用。  
  
 当将其与 `CToolBarCtrl` 对象时，这些工具栏控件使用图像列表。  此关联通过 [CToolBarCtrl::SetImageList](../Topic/CToolBarCtrl::SetImageList.md)[SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)[SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)对、和的调用完成。  
  
 默认情况下，MFC 使用 `CToolBar` 类来实现应用 MFC 程序工具栏。  但是，`GetToolBarCtrl` 成员函数可用于检索嵌入的 `CToolBarCtrl` 对象。  使用返回的对象，然后调用 `CToolBarCtrl` 成员函数。  
  
 下面的示例通过将启用的 \(`m_ToolBarImages`\) 和禁用 \(`m_ToolBarDisabledImages`\) 图像列表演示此方法为 `CToolBarCtrl` 对象 \(`m_ToolBarCtrl`\)。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/CPP/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  工具栏对象使用的图像列表必须是永久对象。  因此，它们通常是 MFC 类的数据成员；在此示例中，主框架窗口类。  
  
 在图像列表与 `CToolBarCtrl` 对象，框架会自动显示适当的按钮图像。  
  
## 请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)