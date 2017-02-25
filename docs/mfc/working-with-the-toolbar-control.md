---
title: "使用工具栏控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl 类, 访问工具栏"
  - "GetToolBarCtrl 方法"
  - "工具栏控件 [MFC], 访问"
  - "工具栏 [C++], 访问公共控件"
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用工具栏控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示了如何访问基础更多控制的对象对 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) [CToolBar](../mfc/reference/ctoolbar-class.md) 工具栏。  这是一个高级主题。  
  
## 过程  
  
#### 若要访问某 CToolBar 的工具栏公共控件对象中  
  
1.  调用 [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)。  
  
 `GetToolBarCtrl` 返回对 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 对象的引用。  可以使用与调用工具栏控件类的成员函数的引用。  
  
> [!CAUTION]
>  如果调用 **设置** 函数，在调用**Get** `CToolBarCtrl` 函数是安全的，请时。  这是一个高级主题。  通常不应需要访问基础工具栏控件。  
  
### 您想进一步了解什么？  
  
-   [使用 Windows 公共控件。](../mfc/controls-mfc.md)  
  
-   [工具栏基本法则](../mfc/toolbar-fundamentals.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [动态调整工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具栏的工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [越过状态栏更新](../mfc/toolbar-tool-tips.md)  
  
-   [处理工具提示通知](../mfc/handling-tool-tip-notifications.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 类  
  
-   [处理自定义通知](../mfc/handling-customization-notifications.md)  
  
-   [多个工具栏](../mfc/toolbar-fundamentals.md)  
  
-   [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
 有关使用 Windows 公共控件的一般信息，请参见 [公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)。  
  
## 请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)