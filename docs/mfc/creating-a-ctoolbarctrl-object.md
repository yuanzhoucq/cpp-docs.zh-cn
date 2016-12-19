---
title: "创建 CToolBarCtrl 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CToolBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl 类, 创建工具栏"
  - "工具栏控件 [MFC], 创建"
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建 CToolBarCtrl 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 对象包含几个数据结构 \- 图像按钮位图按钮列表，标签字符串列表和列表 `TBBUTTON` 结构\-\-该关联图像和字符串与按钮的样式、位置、状态和命令 ID。  每一个数据结构。元素的从零开始的索引引用。  在使用 `CToolBarCtrl` 对象之前，必须建立数据结构。  有关数据结构的列表，请参阅《[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [工具栏控件](https://msdn.microsoft.com/en-us/library/47xcww9x.aspx)。  字符串列表可能为按钮标签只使用；无法从工具栏检索字符串。  
  
 为了使用 `CToolBarCtrl` 对象，您通常执行以下步骤：  
  
### 使用 CToolBarCtrl 对象  
  
1.  构造记录[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 集对象。  
  
2.  调用 [创建](../Topic/CToolBarCtrl::Create.md) "窗口工具栏创建公共控件并将其附加到 `CToolBarCtrl` 对象。  如果希望按钮的位图图像，请添加到工具栏按钮位图。通过调用 [AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md)。  如果希望按钮的标签字符串，请将该字符串添加到工具栏和通过调用 [AddString](../Topic/CToolBarCtrl::AddString.md) [AddStrings](../Topic/CToolBarCtrl::AddStrings.md)。  在调用 `AddString` 和 `AddStrings`后，您应调用 [自动调整大小](../Topic/CToolBarCtrl::AutoSize.md) 以获取字符串或字符串出现。  
  
3.  将按钮添加到工具栏结构通过调用 [AddButtons](../Topic/CToolBarCtrl::AddButtons.md)。  
  
4.  如果需要工具提示，请在工具栏的所有者窗口的 **TTN\_NEEDTEXT** 消息如 [处理工具提示通知](../mfc/handling-tool-tip-notifications.md)所述。  
  
5.  如果希望用户可以自定义工具栏，请处理在所有者窗口的自定义消息通知如 [通知处理自定义](../mfc/handling-customization-notifications.md)所述。  
  
## 请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)