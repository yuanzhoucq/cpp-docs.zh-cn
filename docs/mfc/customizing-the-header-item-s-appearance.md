---
title: "自定义标题项的外观 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CHeaderCtrl 类, 自定义项"
  - "HDS_ 样式"
  - "标题控件, 项的自定义"
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自定义标题项的外观
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过设置参数，*dwStyle* 首次创建标题控件时 \([CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md)\)，可以定义项标头外观和行为或标题控件。  
  
 下面是您可以设置样式的示例及其用途：  
  
-   若要使标题项显示按钮，请使用 `HDS_BUTTONS` 样式。  
  
     请使用此样式，则若要执行操作来响应某标题项上单击，如排序数据由特定列中，Microsoft Outlook。  
  
-   若要为标题项“\) 的热跟踪”外观，当鼠标光标将位于这些项时，使用 `HDS_HOTTRACK` 样式。  
  
     热跟踪显示一个三维轮廓作为通过一项的指针传递在其他方式扁杆。  
  
-   若要指示应隐藏标题控件，使用 `HDS_HIDDEN` 样式。  
  
     `HDS_HIDDEN` 样式指示标题控件旨在用作数据容器而不是可视化控件。  此样式不自动隐藏控件，但是，实际上，会影响 `CHeaderCtrl::Layout`行为。  在 `WINDOWPOS` 结构的 **cy** 成员返回的值将为零控件不应该对用户可见。  
  
 有关这些属性的更多信息，请参见 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中的[Items](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  有关添加项的信息。标题控件，请参见 [标题控件添加项。](../mfc/adding-items-to-the-header-control.md)。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)